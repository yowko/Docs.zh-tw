---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: d43dfccd9735ce1ab822d7b14de2abaa0940c77b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166595"
---
# <a name="oracle-bfiles"></a>Oracle BFILE

Oracle 的 .NET Framework 資料提供者包括 <xref:System.Data.OracleClient.OracleBFile> 類別，可用來與 Oracle <xref:System.Data.OracleClient.OracleType.BFile> 資料型別搭配使用。  
  
 Oracle **BFILE** 資料類型是 oracle **LOB** 資料類型，其中包含大小上限為 4 gb 之二進位資料的參考。 Oracle **BFILE** 與其他 oracle **LOB** 資料類型不同，因為它的資料會儲存在作業系統的實體檔案中，而不是儲存在伺服器上。 請注意， **BFILE** 資料類型會提供資料的唯讀存取權。  
  
 **BFILE**資料類型與**LOB**資料類型區別的其他特性如下：  
  
- 包含非結構化資料。  
  
- 支援伺服器端區塊。  
  
- 使用參考複製語意。 例如，如果您在 **bfile**上執行複製作業，則只會複製 (的 **bfile** 定位器，也就是檔案) 的參考。 而不會複製檔案中的資料。  
  
 您應該使用 **BFILE** 資料類型來參考大小很大的 lob，因此無法實際儲存在資料庫中。 相較于**LOB**資料類型，使用**BFILE**資料類型時，會涉及更多的用戶端、伺服器和通訊負擔。 如果您只需要取得少量的資料，就可以更有效率地存取 **BFILE** 。 如果您需要取得整個物件，則存取常駐於資料庫的 LOB 會更有效率。  
  
 每個非 Null 的 **OracleBFile** 物件都與定義基礎實體檔案位置的兩個實體相關聯：  
  
1. Oracle DIRECTORY 物件 (檔案系統中目錄的資料庫別名) 及  
  
2. 基礎實體檔案的檔名 (位於與 DIRECTORY 物件相關聯的目錄中)。  
  
## <a name="example"></a>範例  

 下列 c # 範例示範如何在 Oracle 資料表中建立 **BFILE** ，然後以 **OracleBFile** 物件的形式來取得它。 此範例將示範如何使用 <xref:System.Data.OracleClient.OracleDataReader> 物件和 **OracleBFile** **Seek** 和 **Read** 方法。 請注意，若要使用此範例，您必須先在 Oracle 伺服器上建立名為 "c： \\ \bfiles" 的目錄和名為 "MyFile.jpg" 的檔案。  
  
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
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](oracle-and-adonet.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
