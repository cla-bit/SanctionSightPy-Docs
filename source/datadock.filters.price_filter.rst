========================
price_filter module
========================

.. py:module:: price_filter

PriceRangeFilter
-------------------


.. class:: PriceRangeFilter(column, set_price=None, min_price=None, max_price=None)

    A filter that restricts rows in a PyArrow table based on numeric price values in a specified column.

    This filter allows either an exact price match, a minimum/maximum price range, or both.
    Only rows that satisfy all specified price conditions are included in the result.

    :param column: The name of the numeric column to apply the filter to.
    :type column: str
    :param set_price: Optional exact value to match.
    :type set_price: Optional[float]
    :param min_price: Optional minimum value (inclusive).
    :type min_price: Optional[float]
    :param max_price: Optional maximum value (inclusive).
    :type max_price: Optional[float]

    .. method:: apply(data)

        Apply the price filter to the given PyArrow table.

        The method filters the input table based on the specified price criteria.
        Conditions are combined with logical AND when both min and max prices are defined.

        :param data: The input PyArrow table to filter.
        :type data: pyarrow.Table
        :return: A filtered PyArrow table containing only the rows that match the price constraints.
        :rtype: pyarrow.Table

        **Example:**

        .. code-block:: python

            # Filter for rows with price between 1000 and 5000
            filter = PriceRangeFilter(column="amount", min_price=1000, max_price=5000)
            filtered_data = filter.apply(data_table)

            # Filter for rows with exact price of 2500
            exact_filter = PriceRangeFilter(column="amount", set_price=2500)
            exact_data = exact_filter.apply(data_table)
