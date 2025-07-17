# Glossary

| Term | Definition |
|------|------------|
| **Activity** | A unit of work that provides context for filesystem changes. Activities can be activated, deactivated, and relocated between workspaces. |
| **Activity Activation** | The process of setting an activity as the active context for recording filesystem changes in a workspace. Only one activity can be active in a workspace at a time. |
| **Activity Deactivation** | The process of removing an activity as the active context in a workspace, recorded with a timestamp. |
| **Activity Relocation** | The process of moving an activity from one workspace to another, which is the only mechanism for synchronizing content between workspaces. |
| **Authentication Session** | A security context that identifies the user performing operations in the system. |
| **Binary Content Delta** | A record of differences between binary file versions stored using the VCDiff format. |
| **Checkpoint** | A user-initiated record of filesystem state differences compared to the previous checkpoint, created while an activity is active. |
| **Checkpoint Transaction** | An atomic operation that records all filesystem changes as part of a single, consistent unit of work. |
| **CLI Client** | Command-line interface client that performs filesystem analysis and interacts with the system. |
| **Common SHA Ancestor** | A shared point in the SHA history of two files, indicating they evolved from the same content. |
| **Content-Addressable Storage (CAS)** | A storage method where file content is indexed and retrieved using its SHA256 hash. |
| **Content Delta** | A record of differences between two versions of a file, containing the prior SHA and current SHA. |
| **Content Summary** | A record created by system administrators to mark content that can be moved to offline storage. |
| **Content Type** | Classification of file content as either TEXT or BINARY, determined when a file is first encountered. |
| **Delta** | A record of differences between two versions of a file. |
| **File** | A filesystem item that contains content and has metadata such as name and path. |
| **FileChange Checkpoint** | A record indicating that a file's content has changed, including its new SHA256 hash. |
| **File Deletion** | A record indicating that a file has been removed from the filesystem. |
| **File Metadata** | Information about a file such as its name and path, used to identify corresponding files across workspaces. |
| **File Relocation** | A record indicating that a file has been moved from one folder to another. |
| **Filesystem Analysis** | The process performed by the CLI client to detect changes in the filesystem by comparing current state with prior state. |
| **Folder** | A filesystem item that can contain files and other folders. |
| **Folder Deletion** | A record indicating that a folder has been removed from the filesystem. |
| **Folder Relocation** | A record indicating that a folder has been moved from one location to another. |
| **Ignored Files** | Files that match specified patterns and are excluded from filesystem analysis and checkpoints. |
| **IgnoredFilesGlobDeclaration** | A record specifying a pattern (glob) for files that should be ignored by the system. |
| **IgnoredFilesGlobDeprecation** | A record indicating that a previously declared ignore pattern is no longer active. |
| **MIME Type** | A standard for identifying file types, used to determine if a file is text or binary. |
| **Offline Content** | Content that has been moved to secondary storage to conserve space, referenced by a ContentSummary. |
| **Prior Checkpoint** | A reference to the checkpoint that occurred immediately before the current one in a transaction. |
| **Renaming** | A record tracking the change of a name for an item, with reference to its prior name. |
| **SHA Ancestor** | A previous version of a file's content identified by its SHA256 hash. |
| **SHA History** | The chronological sequence of SHA256 hashes representing the evolution of a file's content. |
| **SHA Lineage** | The historical relationship between different versions of a file's content, tracked using SHA256 hashes. |
| **SHA256** | A cryptographic hash function that generates a unique 256-bit (32-byte) signature for a piece of data. |
| **Stale Content** | A situation where the source workspace's current SHA is in the SHA lineage of the target workspace's current SHA, indicating the source has older content. |
| **Text Content Delta** | A record of differences between text file versions stored using the UniDiff format. |
| **Transaction** | An atomic unit of work that either completes entirely or is rolled back completely to maintain system consistency. |
| **Trivial Change** | A change where the source workspace's content has the target workspace's current SHA in its history, allowing relocation to proceed. |
| **UniDiff** | A format for representing differences between text files, used for delta storage of text file changes. |
| **User Event** | A record of an action performed by a user, including a timestamp and authentication session. |
| **VCDiff** | A format for representing differences between binary files, used for delta storage of binary file changes. |
| **Workspace** | An environment where files and folders are stored and modified. Multiple workspaces can exist in the system. |
| **Workspace Item** | A generic term for either a file or folder within a workspace. |
| **Workspace Item Deletion** | A record indicating that a workspace item (file or folder) has been deleted. |
| **Workspace Item Relocation** | A record indicating that a workspace item (file or folder) has been moved. |
| **Workspace Renaming** | A record tracking the change of a workspace's name. |