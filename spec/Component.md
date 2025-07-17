
  Components "exist in a void". They are conceptual containers for a portion of a software development effort.

  A manifestation of a component is a set of folders and files within them that evolve over time.
  Manifestations only occur "phisically" in some workspace. They "become interesting" only when
  they appear in a workspace designated to be an "integration workspace" that is just an ordinary workspace
  but a social contract make it become of special interest.

  since components are meant to co-exist in a physical filesystem eventually, special care must be taken
  so the folders in them dont overlap

  The current state of a file in the local filesystem is captured periodically in the scm via a checkpoint operation
  that records any metadata refactoring thay may have occurred (relocation to another folder, file being renamed) or
  content change. All file checkpoints must occur in the context of an activity.