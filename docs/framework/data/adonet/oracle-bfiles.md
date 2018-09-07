---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 683b4a9be826e1d0d4ee354fada10168d833e3d7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087572"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="b8b7a-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="b8b7a-102">Oracle BFILEs</span></span>
<span data-ttu-id="b8b7a-103">Oracle 的 .NET Framework 資料提供者包括 <xref:System.Data.OracleClient.OracleBFile> 類別，可用來與 Oracle <xref:System.Data.OracleClient.OracleType.BFile> 資料型別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="b8b7a-104">Oracle **BFILE**資料類型是一種 Oracle **LOB**資料類型，包含最大值 4 gb 之二進位資料的參考。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="b8b7a-105">Oracle **BFILE**不同於其他 Oracle **LOB**資料類型，因為其資料會儲存在伺服器上的實體檔案而不是作業系統中。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="b8b7a-106">請注意， **BFILE**資料類型提供唯讀存取資料。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="b8b7a-107">其他特性**BFILE**資料類型，使其有別**LOB**資料類型包括：</span><span class="sxs-lookup"><span data-stu-id="b8b7a-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="b8b7a-108">包含非結構化資料。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="b8b7a-109">支援伺服器端區塊。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="b8b7a-110">使用參考複製語意。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-110">Uses reference copy semantics.</span></span> <span data-ttu-id="b8b7a-111">例如，如果您在執行複製作業**BFILE**，則僅**BFILE**複製 （也就是檔案的參考） 的定位器。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="b8b7a-112">而不會複製檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="b8b7a-113">**BFILE**資料類型應該用於參考中的大型的 Lob，因此，不實際儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="b8b7a-114">使用時，會牽涉到更多的用戶端、 伺服器及通訊額外負荷**BFILE**相較於資料類型**LOB**資料型別。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="b8b7a-115">若要存取更有效率**BFILE**如果您只需要取得少量的資料。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="b8b7a-116">如果您需要取得整個物件，則存取常駐於資料庫的 LOB 會更有效率。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="b8b7a-117">每個非 NULL **OracleBFile**物件會定義基礎實體檔案的位置的兩個實體與關聯：</span><span class="sxs-lookup"><span data-stu-id="b8b7a-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="b8b7a-118">Oracle DIRECTORY 物件 (檔案系統中目錄的資料庫別名) 及</span><span class="sxs-lookup"><span data-stu-id="b8b7a-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="b8b7a-119">基礎實體檔案的檔名 (位於與 DIRECTORY 物件相關聯的目錄中)。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b7a-120">範例</span><span class="sxs-lookup"><span data-stu-id="b8b7a-120">Example</span></span>  
 <span data-ttu-id="b8b7a-121">下列 C# 範例示範如何建立**BFILE**在 Oracle 資料表中，然後再擷取它的形式**OracleBFile**物件。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="b8b7a-122">此範例示範如何使用<xref:System.Data.OracleClient.OracleDataReader>物件和**OracleBFile** **搜尋**並**讀取**方法。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="b8b7a-123">請注意，若要使用此範例中，您必須先建立名為"c:\\\bfiles"和 Oracle 伺服器上名為"MyFile.jpg"的檔案。</span><span class="sxs-lookup"><span data-stu-id="b8b7a-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8b7a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8b7a-124">See Also</span></span>  
 [<span data-ttu-id="b8b7a-125">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8b7a-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="b8b7a-126">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b8b7a-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
