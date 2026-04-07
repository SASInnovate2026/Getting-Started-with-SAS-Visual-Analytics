# Demo: Explore and Visualize with SAS Visual Analytics

1. If necessary, from the Desktop, open Google Chrome and click on the **SAS Viya** bookmark.

1. If necessary, log on to SAS Viya using the credentials **Student** and **Metadata0**.

1. To open Visual Analytics, click the **Applications** menu in the upper left corner and select **Explore and Visualize**.

## Access Data

1. From the welcome window, you can open an existing report or create a new report. Select **New report**.

1. Visual Analytics consists of three main areas: the left pane with icons for working with the overall report, a canvas where you build the report, and a right pane with icons for working with specific objects. The canvas displays one or more page tabs across the top of the report.

    **Note:**    Expand the left and right panels to view descriptive labels for each of the icons.

1. Reports use data that is loaded into memory. In the Data pane, there are options to either add data or import data. Click **Import data** > **Local files** and notice that you can load files from the local operating system, such as Microsoft Excel or CSV files. Select **Cancel** > **Cancel**.

1. Click **Add data** to select from tables that have been loaded into memory. Select the **HOMEEQUITY** table, then click **Add**.  

1. The Data pane displays all the columns, or data items, in the **HOMEEQUITY** table. Data items are organized by type. Character columns and numeric columns with a date format appear as categories. Distinct counts appear next to each category. Numeric variables appear as measures.

1. You may also see other icons next to data items. If you had analyzed this table in SAS Information Catalog, columns might be flagged as *Private*, *Sensitive*, or *Candidate*. Those information privacy indicators are displayed in Visual Analytics. The icons next to the Measure data items indicate that outliers may impact aggregation statistics.

## Prepare Data

1. The Data pane is used to modify or create new data items. We learned previously in SAS Information Catalog that in the **Loan Status** column, the value *0* represents a loan in good standing, and *1* is a loan that has defaulted. The values of **Loan Status** represent a binary response rather than a measure. Click <img src='./images/Unfold.svg' height='10px'> </img> (**Edit Properties**) next to **Loan Status** to edit the data item properties. Change **Name** to *Loan Status Code* and **Classification** to *Category*. This data item now appears in the Category group and includes two distinct values.

1. A consumer of this report might not know what the *0* and *1* values represent. We can create a new data item that assigns more descriptive labels to the raw loan status codes. Right-click **Loan Status Code** and select **New Custom Category**.

1. Enter *Loan Status* in the **Name** field. The first group name will be *Paid*. In the **Values** field, enter *0* and press the Enter key. Click **Add group** and enter *Default* in the **Name** field. To show an alternative method for assigning values, click <img src='./images/Edit.svg' height="10px"> </img>  (**Choose values**), move *1* to the Selected items list, then click **OK**. Expand **Remaining Values** and select **Show as missing**, and then click **OK**. Now we can choose to use either the raw loan status codes or descriptive labels in our report.

1. There are many other ways to alter or create new data items. For example, eventually we will view the number of loan applications for each month and year. In the Data pane, expand the properties of **Loan Application Date** and click <img src='./images/Edit.svg' height="10px"> </img> (**Edit**) next to the **Format** field. The current format displays the month name, the 2-digit day, and the four-digit year. Instead, select the **MMMYYYY** format so that the displayed values are the three-letter month and four-digit year. Click **OK**.

1. Notice there is a column named **State**. To map values based on the US state, expand the properties for **State** and change **Classification** to *Geography*. In the Edit Geography Item window, change **Name or code context** to *US State Names*, and 100% of the data values are mapped to the appropriate geographical region. Click **OK**.

1. Finally, hover the cursor over each of the data items in the Measure category. Notice that the default aggregation for all measures, with the exception of Frequency, is SUM. This means that as we build visualizations that include these measures, the summarized values will be totals. Because each row in the data is a separate loan, it makes more sense to look at the average for all measures.  To change the aggregation method, select the check box for each measure. Or select at least one measure data item and select the **More** menu to the right of the New data item button.  Choose **Select** > **Select measures with same aggregation**. Right-click over the selected data items and change **Aggregation** to **Average**.

1. The modifications made to the data items from the **HOMEEQUITY** table are saved as part of this report and do not change the underlying data. However, if you would like to create a reusable and shareable template for a data source that can be applied in other reports? Click <img src='./images/IndicatorData.svg' height="10px"> </img> (**Data source menu**) and select **Save data view**. You can save a personal copy of the view, or if you have appropriate administrative permissions, you can publish the data view for other report creators to use. Saved views can be easily applied by selecting <img src='./images/IndicatorData.svg' height="10px"> </img> (**Data source menu**) and **Manage data views**. Click **Cancel**.

## Explore Data

1. To begin by examining the raw data, select the Objects pane on the left side and then drag **List Table** onto the canvas. On the right side of the canvas, select the Roles pane. Select **Add** next to **Columns** and then choose **Select all** > **Apply**. Drag **Loan Status** to the top of the list so that it's the first column.

1. You can scroll to view the different columns and values, or click on any of the columns, such as **State**, to sort the table in ascending or descending order.

1. If you right-click on a column, there are several additional options. Right-click **Age of Oldest Credit Line** and select **Add cell visualization** > **Bar**. Right-click **Amount of Loan Request** and select **Add cell visualization** > **Heat map**. You can customize cell visualization in the Options pane.

1. Double-click **Page1** at the top of the report and type *Home Equity Data* to name the report page.

1. Next, we'll create a collection of graphs to explore the data. At the top of the canvas, click the plus sign to create a new page. From the Data pane, drag **Loan Status** to the canvas. An autochart is generated, which means that Visual Analytics selects an appropriate graph based on the data type and values. In this example, the autochart is a bar chart.  

1. The autochart can be easily changed to another visualization. Select <img src='./images/Actions.svg' height="10px"> </img> (**Object menu**) in the upper right corner of the bar chart and select **Change bar chart to** > **Pie chart**. In the Options pane, expand the Pie section. Under the Data Labels section, select **Percent of total values** and increase the **Text style** size to **12**. The chart indicates that approximately 20% of the loans default.

1. In the Data pane, select **Amount of Loan Request** and drag it to the right side of the canvas. The autochart is a histogram, which is a great way to view the distribution of the values.

1. Next, drag **Loan Application Date** below the histogram. This time, the autochart is a line plot that tracks the frequency of loan applications over time. This downward trend is expected because homeowners were more likely to refinance rather than apply for home equity loans during these years of declining interest rates.  

1. You don't have to always start with an autochart to create a report item. From the Objects pane, you can select from a long list of options. Drag **Bar Chart** below the pie chart. You can use either the Assign Data button or the Data Roles pane to build the graph. Add **Job Category** to the Category role. Under Measure, remove **Frequency** and then add **Amount Due on Existing Mortgage** and **Value of Current Property**. The length of each bar represents the average measure because we previously changed the aggregation.

1. You can further customize the graph by selecting the Options pane. Expand the **Bar** category and change the direction to **vertical**.

1. These static images are informative, but it would be helpful to see how they differ by region. In the Data pane, right-click **Region** and select **Add as a page control**. Now you can click each Region button to see how the graphs change.

1. This page is a good first step to understand our home equity data. Double-click the **Page 2** label and enter *Loan Exploration*.

1. Let's dive a bit deeper into the geography data. Create another new page, then double-click **Page 3** label and type *Geo Analysis*. Select **State** in the Data pane and drag it to the canvas. A map is created. Select the Roles pane on the right and add **Frequency** to the Size role and **Amount of Loan Request** to the Color role.

1. Return to the Data pane and select **New data item** > **Hierarchy**. A hierarchy enables you to drill into categories within your data. Add the largest grouping first, which is **Region** with four values. Then add **Division**, followed by **State**. Notice that the **Name** field automatically includes the hierarchy values. Click **OK**.

1. Drag the **Region -- Division -- State** hierarchy to the left side of the canvas, and Visual Analytics creates a bar chart. You can click on each bar label to drill into **Region** and **Division** to see the corresponding frequency of loans.

1. Select the **Actions** icon in the right panel to link the map and bar chart. In the Actions pane, select the check box for **Geo coordinate -- State 1**. Each time that you drill into a particular bar on the Region chart, the map updates based on the filtered data.   

## Explain and Analyze Data

1. We've explored this historical loan data, but the next question is: How does the data help to predict **Loan Status**? Return to the Data pane, and then right-click **Loan Status** and select **Explain** > **Explain on new page**. Visual Analytics generates an automated explanation that indicates that the three factors most related to **Loan Status** are **Debt** **to Income Ratio**, **Number of Delinquent Credit Lines**, and **Value of Current Property**. Double-click the **Page 4** label and name this page *Predict Loan Status*.

1. Visual Analytics enables you to create a preliminary model to predict **Loan Status.** Click the Object menu in the upper right corner of the page and select **Duplicate as** > **Gradient boosting**. This model enables us to continue in the analytics life cycle. The Options pane enables you to customize and fine-tune the model.

    **Note:**    The **Create Pipeline** button hands the model off to Model Studio for deeper analysis and model comparison.

## Save and View the Report

1. Click <img src='./images/Save.svg' height="10px"> </img> (**Save**) and select **My Folder**. Name the report **Home Equity Report** and click **Save**. Replace the report if necessary. The report is currently in Edit mode, so click the **View report** button in the upper left corner. Select the **Loan Exploration** page and confirm that all the charts update as you select each region. Select the **Geo Analysis** page and verify that the map updates as you select a bar representing a particular geographic area.

1. In the upper right corner of Visual Analytics, select **Opened reports** and click **Close all reports**.

1. We've packed a lot into this report, but we've just scratched the surface of what is possible in SAS Visual Analytics. If you would like to view other completed sample reports with even more objects and actions, navigate to **SAS Content** > **Products** > **SAS Visual Analytics** > **Samples**.

1. To learn more, select <img src='./images/HelpButtonToolbar.svg' height="10px"> </img> (**Help**) and visit the Learning Center. There are several resources available for you to expand your Visual Analytics expertise.