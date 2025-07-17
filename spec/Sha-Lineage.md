
  # SHA Lineage

    Activity relocation is an edge in a directed graph where the nodes are workspaces.
    The system is consistent in that the only way to synchronize content between workspaces
    is activity relocation.

    The relocation starts a transacion that could end up with rollback.

    The system analyzes if it is currently possible for an activity to relocate to another workspace
    by checking if it can find evidence about sha-lineage between files with the same metadata
    in different workspaces (same name in the same folder).
    The system tracks the changes for each file in each workspace, so it knows if the file
    had a certain content at some point in time (shas were recorded for each file content change).
    If at relocation request time it finds that a file with a name and located in a folder
    have different shas, it can analyze if both share a sha ancestor.

    For logical reasons what is expected is that the file in the source workspace would have updated
    content in relation to the target workspace. the system knows when changes happened and it would
    inform about any anomalies like attempting to "update" the target workspace with "stale" content
    from the source workspace. Stale content is the situation where current source sha content
    is in the sha lineage of the target current sha content. The checkpoint will be interrupted.
    The user may choose to override this by referring to the "stale" sha in the command line for the
    checkpoint request. this is so the user can intentionally force the old content to be applied
    on top of the new content.
    The "normal"/"expected" situation is that the source workspace
    has the latest interesting content, so the source content would have the target current sha
    in its change history sequence. If so, this is considered a trivial change and the relocation
    evaluation can continue. If no sha lineage was found, the relocation evaluation is aborted
    and the transacion fails.
