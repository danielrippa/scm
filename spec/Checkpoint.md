
  # FileSystem Item Checkpoints

    A user is expected to request checkpoints frequently. A checkpoint can be requested because
    the user wants to record an interesting state before experiments start, or he just wants
    to make sure the current state is recorded at end of work day. So many checkpoints are expected daily.
    The system will not nudge the user into checkpointing. The system trusts the user judgement.

    No checkpoint can be recorded unless an Activity is active in the current workspace.

    FileSystem Item checkpoint is the act of recording in the system changes detected in the filesystem and
    record the fact that an Activity was active at that moment in time.

    A FileSystem Item can be either a File or a Folder.
    A Folder Checkpoint can consist of either a creation, a deletion, a relocation, or a renaming.
    A File Checkpoint add the notion of a Content Change that is another element of a file checkpoint.

    Since this transaction is the opportunity to record changes in the filesystem some
    checkpoints cannot co-exist like creation and deletion (because deletion is recorded due to the
    absence of the file, so its illogical that the system detected a creation and a deletion at the same time).

    The act of recording those changes is sequential and part of a transaction that could fail.
    The sequence is recorded by stating in each checkpoint record which checkpoint record happened before
    in this transaction (except the first checkpoint, which has no prior).

    For example, in a previous checkpoint a file existed but now the system detects
    the file is not available anymore, so the a FileCheckpointDeletion record must be created.

