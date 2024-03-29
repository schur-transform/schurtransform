Using GAP to calculate character tables
---------------------------------------
Out of the box, this package provides the character tables and projectors up to degree 6, that is for the symmetric group S6. In special cases, you may want to use higher degree. Use the instructions below to do so.

Character tables are computed with `GAP <https://www.gap-system.org/>`_ (the Groups, Algorithms, and Programming computer algebra system). We used GAP version 4.11.1. You can install GAP on your computer by following the `installation instructions <https://www.gap-system.org/Download/index.html>`_. Ensure ``gap`` is on the path.

Then use the following script, which is installed with the ``schurtransform`` package, with the number 8 replaced by the desired degree::

    regenerate-symmetric-group-characters --max-degree 8

Files ``s2.csv``, ``s3.csv``, ... will be created, as well as a table ``symmetric_group_conjugacy_classes.csv`` with additional information about the rows and columns. These files can then be supplied to the :py:func:`.transform` function.

The contents of ``s3.csv`` look like this:

+-------+-------+-----+----+
|       | 1+1+1 | 2+1 | 3  |
+=======+=======+=====+====+
| 1+1+1 | 1     | 1   | 1  |
+-------+-------+-----+----+
| 2+1   | 2     | 0   | -1 |
+-------+-------+-----+----+
| 3     | 1     | -1  | 1  |
+-------+-------+-----+----+

Each row provides the values of one irreducible character function. Care was taken to ensure that these rows are appropriately labelled by integer partitions. The desire to ensure this was one reason that we opted to use GAP directly rather than the SageMath wrapper around GAP. (See related `discussion <https://math.stackexchange.com/questions/2348878/labels-for-irreducible-symmetric-group-characters>`_.)

The contents of ``symmetric_group_conjugacy_classes.csv`` look like this:

+---------------+---------+--------------------+
|Symmetric group|Partition|Conjugacy class size|
+===============+=========+====================+
|S2             |1+1      |1                   |
+---------------+---------+--------------------+
|S2             |2        |1                   |
+---------------+---------+--------------------+
|S3             |1+1+1    |1                   |
+---------------+---------+--------------------+
|S3             |2+1      |3                   |
+---------------+---------+--------------------+
|S3             |3        |2                   |
+---------------+---------+--------------------+
|S4             |1+1+1+1  |1                   |
+---------------+---------+--------------------+
|S4             |2+1+1    |6                   |
+---------------+---------+--------------------+
|S4             |2+2      |3                   |
+---------------+---------+--------------------+
|S4             |3+1      |8                   |
+---------------+---------+--------------------+
|S4             |4        |6                   |
+---------------+---------+--------------------+
|S5             |1+1+1+1+1|1                   |
+---------------+---------+--------------------+
|...            |...      |...                 |
+---------------+---------+--------------------+
