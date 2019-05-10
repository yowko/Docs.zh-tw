---
title: Oracle 序列
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 4ba7b750d48613b80eca0ef3c7c2da127977498d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64632335"
---
# <a name="oracle-sequences"></a>Oracle 序列
.NET Framework Data Provider for Oracle 藉由使用 <xref:System.Data.OracleClient.OracleDataAdapter>，支援在執行插入後擷取伺服器所產生的「Oracle 序列」索引鍵值。  
  
 SQL Server 和 Oracle 都支援自動遞增資料行的建立 (您可將這些資料行指定為主索引鍵)。 上述的值會在資料列加入至資料表時由伺服器產生。 在 SQL Server 中要設定資料行的「識別」屬性；在 Oracle 中則要建立「序列」(Sequence)。 SQL Server 中的自動遞增資料行與 Oracle 中的序列差別在於：  
  
- 在 SQL Server 中，您要將資料行標示為自動遞增資料行，而 SQL Server 會在您插入新資料列時自動產生資料行的新值。  
  
- 在 Oracle 中，您要建立序列，以針對資料表中的資料行產生新值，但序列和資料表或資料行之間並沒有直接連結。 Oracle 序列是一種物件，類似資料表或預存程序 (Stored Procedure)。  
  
 當您在 Oracle 資料庫中建立序列時，可以定義其初始值及值之間的遞增值。 也可以在提交新資料列之前，查詢新值的序列。 這表示您的程式碼可在您將新資料列的索引鍵值插入資料庫之前先加以辨識。  
  
 如需使用 SQL Server 和 ADO.NET 建立自動遞增資料行的詳細資訊，請參閱[擷取識別或自動編號值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)並[建立自動遞增資料行](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)。  
  
## <a name="example"></a>範例  
 下列的 C# 範例示範如何從 Oracle 資料庫擷取新的序列值。 此範例會參考用來提交新資料列的 INSERT INTO 查詢中的序列，然後傳回使用 Oracle10g 所引進的 RETURNING 子句產生的序列值。 此範例使用 ADO.NET 的自動遞增功能來產生「預留位置」主索引鍵值，在 <xref:System.Data.DataTable> 中加入暫止的新資料列序列。 請注意，ADO.NET 為新資料列所產生的遞增值只是「預留位置」， 這表示資料庫可能會從 ADO.NET 所產生的值產生不同的值。  
  
 此範例會在暫止的插入提交至資料庫之前，先顯示資料列的內容。 接著程式碼會建立新的 <xref:System.Data.OracleClient.OracleDataAdapter> 物件，然後設定其 <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> 和 <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> 屬性。 此範例也透過輸入參數的使用，提供傳回伺服器產生值的邏輯。 此範例接著會執行更新，以提交暫止的資料列並顯示 <xref:System.Data.DataTable> 的內容。  
  
```csharp  
public void OracleSequence(String connectionString)  
{  
   String insertString =   
      "INSERT INTO SequenceTest_Table (ID, OtherColumn)" +  
      "VALUES (SequenceTest_Sequence.NEXTVAL, :OtherColumn)" +  
      "RETURNING ID INTO :ID";  
  
   using (OracleConnection conn = new OracleConnection(connectionString))  
   {  
      //Open a connection.  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
  
      // Prepare the database.  
      cmd.CommandText = "DROP SEQUENCE SequenceTest_Sequence";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "DROP TABLE SequenceTest_Table";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "CREATE TABLE SequenceTest_Table " +  
                     "(ID int PRIMARY KEY, OtherColumn varchar(255))";  
      cmd.ExecuteNonQuery();  
  
      cmd.CommandText = "CREATE SEQUENCE SequenceTest_Sequence " +  
                        "START WITH 100 INCREMENT BY 5";  
      cmd.ExecuteNonQuery();  
  
      DataTable testTable = new DataTable();  
      DataColumn column = testTable.Columns.Add("ID", typeof(int));  
      column.AutoIncrement = true;  
      column.AutoIncrementSeed = -1;  
      column.AutoIncrementStep = -1;  
      testTable.PrimaryKey = new DataColumn[] { column };  
      testTable.Columns.Add("OtherColumn", typeof(string));  
      for (int rowCounter = 1; rowCounter <= 15; rowCounter++)  
      {  
         testTable.Rows.Add(null, "Row #" + rowCounter.ToString());  
      }  
  
      Console.WriteLine("Before Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      Console.WriteLine();  
  
      cmd.CommandText =   
        "SELECT ID, OtherColumn FROM SequenceTest_Table";  
      OracleDataAdapter da = new OracleDataAdapter(cmd);  
      da.InsertCommand = new OracleCommand(insertString, conn);  
      da.InsertCommand.Parameters.Add(":ID", OracleType.Int32, 0, "ID");  
      da.InsertCommand.Parameters[0].Direction = ParameterDirection.Output;  
      da.InsertCommand.Parameters.Add(":OtherColumn", OracleType.VarChar, 255, "OtherColumn");  
      da.InsertCommand.UpdatedRowSource = UpdateRowSource.OutputParameters;  
      da.UpdateBatchSize = 10;  
  
      da.Update(testTable);  
  
      Console.WriteLine("After Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      // Close the connection.  
      conn.Close();  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
