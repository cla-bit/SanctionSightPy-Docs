=======================================
filters module
=======================================

.. py:module:: sanction


=====================
SanctionService
=====================

.. class:: SanctionService(client)

    A service class for retrieving and processing sanction data from SanctionSightPy.

    This class provides methods to fetch sanction data, apply filters, and convert
    the data to pandas DataFrames for easier analysis.

    :param client: An authenticated client for SanctionClient API access.
    :type client: SanctionClient

    .. method:: get_filtered(agency, filter_items=None)

        Retrieve sanction data for an agency with optional filtering.

        Fetches data from the API and applies the specified filters sequentially.
        Returns the data as a PyArrow Table or a rich viewer for efficient processing and visualization.

        :param agency: The sanction agency code (e.g., ``'uk_sanctions'``).
        :type agency: str
        :param filter_items: Optional list of filter objects to apply to the data.
        :type filter_items: Optional[List[BaseFilter]]
        :return: A PyArrow Table or RichArrowTableViewer containing the filtered data.
        :rtype: Union[pyarrow.Table, RichArrowTableViewer]

        **Example:**

        .. code-block:: python

            service = SanctionService(client)
            all_filters = [DateRangeFilter(min_price=500000), NameFilter(min_bedrooms=3)]
            filtered_data = await service.get_filtered('canada_sanction', all_filters)

    .. method:: to_pandas(state, columns=None)

        Retrieve sanction data and convert it to a pandas DataFrame.

        Gets data for the specified agency (referred to as `state` in the method signature)
        and optionally selects specific columns for analysis.

        :param state: The agency code to fetch data for (e.g., ``'canada_sanction'``).
        :type state: str
        :param columns: Optional list of column names to include in the DataFrame.
                        If ``None``, all columns are included.
        :type columns: Optional[List[str]]
        :return: A pandas DataFrame containing the sanction data.
        :rtype: pandas.DataFrame

        **Example:**

        .. code-block:: python

            service = SanctionService(client)
            df_result = await service.to_pandas('canada_sanction', columns=['entity', 'last_name'])
            print(df_result.head())
