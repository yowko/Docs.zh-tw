---
title: Oracle BFILE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7e7b7d438abb5a7e14a55f30447d291d3c8ee286
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-bfiles"></a>Oracle BFILE
Oracle 的 .NET Framework 資料提供者包括 <xref:System.Data.OracleClient.OracleBFile> 類別，可用來與 Oracle <xref:System.Data.OracleClient.OracleType.BFile> 資料型別搭配使用。  
  
 Oracle **BFILE**資料型別是一種 Oracle **LOB**資料類型，包含最大值 4 gb 之二進位資料的參考。 Oracle **BFILE**不同於其他 Oracle **LOB**資料類型，其資料儲存在伺服器上的實體檔案而不是作業系統中。 請注意， **BFILE**資料類型提供唯讀資料存取。  
  
 其他特性**BFILE**資料型別有別於**LOB**資料類型包括：  
  
-   包含非結構化資料。  
  
-   支援伺服器端區塊。  
  
-   使用參考複製語意。 例如，如果您在上執行複製作業**BFILE**，則只**BFILE**複製定位器 （其為檔案的參考）。 而不會複製檔案中的資料。  
  
 **BFILE**資料類型應該用於參照大小，大的 Lob，因此，不適合儲存在資料庫中。 當使用涉及多個用戶端、 伺服器及通訊額外負荷**BFILE**資料型別相較於**LOB**資料型別。 若要存取更有效率**BFILE**如果您只需要取得少量資料。 如果您需要取得整個物件，則存取常駐於資料庫的 LOB 會更有效率。  
  
 每個非 NULL **OracleBFile**物件都與定義基礎實體檔案的位置的兩個實體：  
  
1.  Oracle DIRECTORY 物件 (檔案系統中目錄的資料庫別名) 及  
  
2.  基礎實體檔案的檔名 (位於與 DIRECTORY 物件相關聯的目錄中)。  
  
## <a name="example"></a>範例  
 下列 C# 範例會示範如何建立**BFILE**在 Oracle 資料表中，然後再擷取它的形式**OracleBFile**物件。 此範例示範如何使用<xref:System.Data.OracleClient.OracleDataReader>物件和**OracleBFile** **搜尋**和**讀取**方法。 請注意，若要使用這個範例中，您必須先建立名為"c:\\\bfiles"和 Oracle 伺服器上名為"MyFile.jpg"的檔案。  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
