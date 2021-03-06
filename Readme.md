<!-- default file list -->
*Files to look at*:

* [Form1.cs](./CS/Form1.cs) (VB: [Form1.vb](./VB/Form1.vb))
* [Program.cs](./CS/Program.cs) (VB: [Program.vb](./VB/Program.vb))
<!-- default file list end -->
# How to bind SchedulerControl to an SQL Server database and customize Update/Delete/Insert queries without the use of the SqlCommandBuilder


<p>This example illustrates how to setup SchedulerControl binding at runtime. Note that all appointment mappings and even SQL queries along with their parameters are adjusted in code without the use of the VS designer. This is the most flexible database-binding technique because it allows you to modify data-binding options and SQL queries with ease. For instance, we keep the time of modification along with the modified row by inserting a <a href="http://msdn.microsoft.com/en-us/library/ms188383.aspx"><u>GETDATE</u></a> function result into a <strong>TimeStamp </strong>column. Here are to corresponding SQL queries:</p>


```sql
INSERT INTO CarScheduling (StartTime, EndTime, Subject, TimeStamp) VALUES (@StartTime, @EndTime, @Subject, GetDate())

UPDATE CarScheduling SET StartTime = @StartTime, EndTime = @EndTime, Subject = @Subject, TimeStamp = GetDate() WHERE ID = @ID

DELETE FROM CarScheduling WHERE ID = @ID
```


<p> </p>
<p>To test this example locally, setup "SchedulerBindDynamically" sample database in your SQL Server instance. Utilize the SchedulerBindDynamically.sql file attached to this example to generate a sample database and table schema.</p>
<p><strong>Note:</strong> <br> We do not use the <a href="http://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlcommandbuilder.aspx"><u>SqlCommandBuilder Class</u></a> capabilities to generate SQL queries as it is shown in the <a href="https://www.devexpress.com/Support/Center/p/E551">How to bind SchedulerControl to MS SQL Server database at runtime</a> code example. The <a href="http://msdn.microsoft.com/en-us/library/system.data.common.dbcommandbuilder.conflictoption.aspx"><u>DbCommandBuilder.ConflictOption Property</u></a> option of this class allows you to enable optimistic concurrency to prevent a concurrency violation error. Since we do not use this functionality, you might encounter this error when using this example. Fortunately, there are some ways that allows you to avoid this error. You can find them in the <a href="http://msdn.microsoft.com/en-us/library/cs6hb8k4.aspx"><u>Introduction to Data Concurrency in ADO.NET</u></a> MSDN article.</p>
<p><strong>See Also:</strong><br> <a href="http://msdn.microsoft.com/en-us/library/33y2221y.aspx"><u>Updating Data Sources with DataAdapters</u></a></p>
<p><a href="https://documentation.devexpress.com/WindowsForms/2949/Controls-and-Libraries/Scheduler/Getting-Started">Getting Started</a></p>

<br/>


