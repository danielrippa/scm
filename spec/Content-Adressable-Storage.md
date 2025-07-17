
  # Content Adressable Storage

  The initial content determines the type of content.
  The system analyzed the first moment in time where the file appeared in the workspace and is able
  to determinate wether the file is of text or binary type (as an implementation detail,
  gnu file is used with the --mime-type option and extracting the major type of the mime-type. If
  the major type is text, then the file is considered of type text, and binary otherwise).
  Once determined, a file is not allowed to change its type (it would be illogical).
  If the user deletes a text file and renames an image file to the same name as the textfile,
  and both were previously versioned, the cli client detects this as a binary text renaming and a text
  file deletion and so the checkpoint can continue since this is business as usual.

  Changes to the content of a File are recorded in FileChange checkpoint records.

  For each file in the workspace (minus all "Ignored files") the sha256 is obtained.

  If the current sha is different from the last FileChange checkpoint for that file a FileChange checkpoint record
  will be created.

  File contents are recorded independently of file metadata and indexed by its sha256.
  Initial content for files is recorded verbatim. Subsequent changes are recorded as content deltas.

  Content Deltas for binary and text files are handled differently.
  Since this is a SCM system its expected that the vast majority of files will be of type text,
  but the system can also be used for assent management so binary content is also
  carefully tracked.
  UniDiff is used for text and standard VCDiff is used for binary deltas. This allows for delta storage
  efficiency in both binary and text cases.

  This also allows for storage efficiency since copies of the same file that appear in multiple folders
  and/or different workspaces mean its
  content will be recorded only once in the CAS.

  The system administrator can choose to create summary records for content, so all content from that
  point backwards can be moved to offline storage to keep storage requirements under control.
