========================
date_filter module
========================

.. py:module:: date_filter


DateRangeFilter
----------------


.. class:: DateRangeFilter(date_column, start_date=None, end_date=None)

    A filter that limits rows in a PyArrow table based on a date range in a specified column.

    This class can be used to filter records by comparing date values in a given column
    to a start and/or end date. Both string and datetime inputs are supported.

    :param date_column: The name of the date column to filter on.
    :type date_column: str
    :param start_date: Optional start date for the filter (inclusive). Can be a string or datetime.
    :type start_date: Optional[Union[str, datetime]]
    :param end_date: Optional end date for the filter (inclusive). Can be a string or datetime.
    :type end_date: Optional[Union[str, datetime]]

    .. method:: apply(data)

        Apply the date range filter to the given PyArrow table.

        The method casts the target column to timestamp type and filters rows
        to include only those within the specified date range.

        :param data: The input PyArrow table to filter.
        :type data: pyarrow.Table
        :return: A filtered PyArrow table based on the date constraints.
        :rtype: pyarrow.Table

        **Example:**

        .. code-block:: python

            data_table = pa.table([
                "transfer_date": ["2023-05-12", "2023-01-01", "2022-01-10", "2024-01-01"]
            ])

            filter = DateRangeFilter(
                date_column='transfer_date',
                start_date='2023-01-01',
                end_date='2024-01-01'
            )
            filtered_data = filter.apply(data_table)
