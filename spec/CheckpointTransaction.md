
  # Checkpoint Transactions

  All transactions are performed in a single-thread, synchronous fashion to avoid race conditions.

  Transactions are actual SQL transactions and a COMMIT TRANSACTION will only occur if
  the system can, for example, verify sha lineage between files, etc.

  Since these are actual SQL transactions, no recovery procedures are needed since consistency
  is guaranteed. A transaction can be either committed or rolled back completely.
