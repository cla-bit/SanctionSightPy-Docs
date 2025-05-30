===========================
entity_filter module
===========================

.. py:module:: entity_filter


EntityFilter
--------------


.. class:: EntityFilter(search_terms, columns, match_type='partial', case_sensitive=False)

    A filter that searches for specific terms in one or more columns of a PyArrow table.

    This class supports different match types such as exact match, partial (substring)
    match, or prefix-based matching. Case sensitivity can also be toggled.

    :param search_terms: A single string or list of strings to search for.
    :type search_terms: Union[str, List[str]]
    :param columns: The column name or list of column names to search in.
    :type columns: Union[str, List[str]]
    :param match_type: The type of string matching to use:
                       - ``'partial'``: Substring match (default)
                       - ``'exact'``: Full equality
                       - ``'startswith'``: Match beginning of string
    :type match_type: str
    :param case_sensitive: Whether the match should be case-sensitive.
    :type case_sensitive: bool

    .. method:: apply(data)

        Apply the entity filter to the given PyArrow table.

        For each search term and target column, builds a logical mask and filters
        the table to include only rows matching at least one of the conditions.

        :param data: The input PyArrow table to filter.
        :type data: pyarrow.Table
        :return: A filtered PyArrow table containing only the matching rows.
        :rtype: pyarrow.Table

        **Example:**

        .. code-block:: python

            # Sample data
            data_table = pa.table({
                "name": ["Alice", "Bob", "Charlie", "David", "alice", "Smith", "Johnson"],
                "occupation": ["Engineer", "Doctor", "Artist", "Engineer", "Scientist"]
            })

            filter = EntityFilter(
                search_terms=["Smith"],
                columns=["name"],
                match_type="startswith",
                case_sensitive=False
            )
            filtered_table = filter.apply(data_table)
