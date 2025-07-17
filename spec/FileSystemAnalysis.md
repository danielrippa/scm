
  # FileSystem Analysis

  FileSystem Analysis is performed by the cli client. After analyzing it can deduce a file was moved, or deleted
  or created, etc. It reports the news to the system as it understood them when the user issues a checkpoint request.
  So the cli client may only discover a file deletion by detecting the absence of a file that existed previously.
  It cannot report both absence and creation of the same file, it would be contradictory.
  The cli client queries the system to know the prior state of the filesystem and then proceeds to compare it
  to the current state. It may happen that the user (between checkpoints) could have deleted a file and a
  few days later xcopies it from a backup. At checkpoint time the cli client is unaware that the file was deleted
  and re-created later. It will see the file is still there and maybe detect changes in its contents, so it would
  report a file content change if this latest copy differs from the content previously reported.
  Maybe other file was deleted from a folder and a days later an xcopy is made to another folder.
  The cli client will record this as a re-location of the file to its current folder, because it
  cannot detect the file was deleted and later re-constructed from backup. This is by design and not considered
  a flaw. This is not a filesystem monitoring system. Expecting the user to do the perfect action at all times
  is absurd. This way of intentional checkpoint requests after the user carefully pruned the filesystem
  so the system records the absolute best state is intentional design. Its a feature, not a flaw.
  If the cli detects the file content has a different sha from what was last reported, it will produce
  a delta. The delta will be either a unidiff obtained via GNU Diff -u or a VCDiff obtained via XDelta3.

  Since the analysis subject is an actual filesystem, no circular references are possible.
  The cli client reports to the system the current state, so a folder cannot be located in itself, for example.
