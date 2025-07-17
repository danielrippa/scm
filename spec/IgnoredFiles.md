
  # Ignored File Globs

  The system allows for specification of ignored file globs per component.
  This is convenient for centralized preferences that help with policy consistency.
  The system trusts the user, so if the user issues a deprecation of a file glob declaration
  at the next checkpoint request all files not previously included will be versioned.
  Since this is a potentially distruptive action, the user will be asked for confirmation
  when a checkpoint request is issued after glob deprecation occurred.
  Both glob declaration and deprecation are infrequent, atypical actions.