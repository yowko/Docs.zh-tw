---
title: "Oracle BFILE | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Oracle BFILE
Oracle 的 .NET Framework 資料提供者包括 <xref:System.Data.OracleClient.OracleBFile> 類別，可用來與 Oracle <xref:System.Data.OracleClient.OracleType> 資料型別搭配使用。  
  
 Oracle **BFILE** 資料型別是一種 Oracle **LOB** 資料型別，它包含最大值 4 GB 之二進位資料的參考。  Oracle **BFILE** 與其他 Oracle **LOB** 資料型別的不同之處在於，其資料儲存於作業系統的實體檔案中，而不是儲存於伺服器上。  請注意，**BFILE** 資料型別對資料資料唯讀存取權。  
  
 使 **BFILE** 資料型別有別於 **LOB** 資料型別的其他特性包括：  
  
-   包含非結構化資料。  
  
-   支援伺服器端區塊。  
  
-   使用參考複製語意。  例如，如果您在 **BFILE** 上執行複製作業，則只會複製 **BFILE** 定位器 \(其為檔案的參考\)。  而不會複製檔案中的資料。  
  
 **BFILE** 資料型別應該用來參考無法儲存於資料庫中的大型 LOB。  與 **LOB** 資料型別相比，使用 **BFILE** 資料型別所涉及的用戶端、伺服器及通訊額外負荷較大。  如果您只需要取得少量資料，則存取 **BFILE** 會更有效率。  如果您需要取得整個物件，則存取常駐於資料庫的 LOB 會更有效率。  
  
 每個非 NULL **OracleBFile** 物件都與定義基礎實體檔案位置的兩個實體相關聯：  
  
1.  Oracle DIRECTORY 物件 \(檔案系統中目錄的資料庫別名\) 及  
  
2.  基礎實體檔案的檔名 \(位於與 DIRECTORY 物件相關聯的目錄中\)。  
  
## 範例  
 下列 C\# 範例說明如何在 Oracle 資料表中建立 **BFILE**，然後以 **OracleBFile** 物件的形式擷取。  該範例使用 <xref:System.Data.OracleClient.OracleDataReader> 物件與 **OracleBFile** **Seek** 及 **Read** 方法來進行示範。  請注意，為了使用此範例，您必須先在 Oracle 伺服器上建立名為 c:\\\\bfiles 的目錄及名為 MyFile.jpg 的檔案。  
  
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
  
## 請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)