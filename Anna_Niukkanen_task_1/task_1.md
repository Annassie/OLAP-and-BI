## Task 1

The Task 1 is about creating Exel table and chart based on info from AdventureWork2019-db.

Fot it was selected the next tables:

SELECT WorkOrderID, LocationID, ProductID, ActualStartDate, actualCost <br>
FROM [Production].[WorkOrderRouting] <br>
ORDER BY ActualStartDate, ProductID <br>

Exel table:

![Exel_table](https://github.com/Annassie/OLAP-and-BI/blob/task_1/Anna_Niukkanen_task_1/images/Screenshot%202022-03-24%20at%2015.10.27.png)


Chart:

![Chart_task_1](https://github.com/Annassie/OLAP-and-BI/blob/task_1/Anna_Niukkanen_task_1/images/chart_task_1.png)
