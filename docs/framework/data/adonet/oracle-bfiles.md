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
# <a name="oracle-bfiles"></a><span data-ttu-id="59724-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="59724-102">Oracle BFILEs</span></span>

<span data-ttu-id="59724-103">Oracle 的 .NET Framework 資料提供者包括 <xref:System.Data.OracleClient.OracleBFile> 類別，可用來與 Oracle <xref:System.Data.OracleClient.OracleType.BFile> 資料型別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="59724-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="59724-104">Oracle **BFILE** 資料類型是 oracle **LOB** 資料類型，其中包含大小上限為 4 gb 之二進位資料的參考。</span><span class="sxs-lookup"><span data-stu-id="59724-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="59724-105">Oracle **BFILE** 與其他 oracle **LOB** 資料類型不同，因為它的資料會儲存在作業系統的實體檔案中，而不是儲存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="59724-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="59724-106">請注意， **BFILE** 資料類型會提供資料的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="59724-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="59724-107">**BFILE**資料類型與**LOB**資料類型區別的其他特性如下：</span><span class="sxs-lookup"><span data-stu-id="59724-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="59724-108">包含非結構化資料。</span><span class="sxs-lookup"><span data-stu-id="59724-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="59724-109">支援伺服器端區塊。</span><span class="sxs-lookup"><span data-stu-id="59724-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="59724-110">使用參考複製語意。</span><span class="sxs-lookup"><span data-stu-id="59724-110">Uses reference copy semantics.</span></span> <span data-ttu-id="59724-111">例如，如果您在 **bfile**上執行複製作業，則只會複製 (的 **bfile** 定位器，也就是檔案) 的參考。</span><span class="sxs-lookup"><span data-stu-id="59724-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="59724-112">而不會複製檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="59724-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="59724-113">您應該使用 **BFILE** 資料類型來參考大小很大的 lob，因此無法實際儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="59724-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="59724-114">相較于**LOB**資料類型，使用**BFILE**資料類型時，會涉及更多的用戶端、伺服器和通訊負擔。</span><span class="sxs-lookup"><span data-stu-id="59724-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="59724-115">如果您只需要取得少量的資料，就可以更有效率地存取 **BFILE** 。</span><span class="sxs-lookup"><span data-stu-id="59724-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="59724-116">如果您需要取得整個物件，則存取常駐於資料庫的 LOB 會更有效率。</span><span class="sxs-lookup"><span data-stu-id="59724-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="59724-117">每個非 Null 的 **OracleBFile** 物件都與定義基礎實體檔案位置的兩個實體相關聯：</span><span class="sxs-lookup"><span data-stu-id="59724-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="59724-118">Oracle DIRECTORY 物件 (檔案系統中目錄的資料庫別名) 及</span><span class="sxs-lookup"><span data-stu-id="59724-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="59724-119">基礎實體檔案的檔名 (位於與 DIRECTORY 物件相關聯的目錄中)。</span><span class="sxs-lookup"><span data-stu-id="59724-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59724-120">範例</span><span class="sxs-lookup"><span data-stu-id="59724-120">Example</span></span>  

 <span data-ttu-id="59724-121">下列 c # 範例示範如何在 Oracle 資料表中建立 **BFILE** ，然後以 **OracleBFile** 物件的形式來取得它。</span><span class="sxs-lookup"><span data-stu-id="59724-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="59724-122">此範例將示範如何使用 <xref:System.Data.OracleClient.OracleDataReader> 物件和 **OracleBFile** **Seek** 和 **Read** 方法。</span><span class="sxs-lookup"><span data-stu-id="59724-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="59724-123">請注意，若要使用此範例，您必須先在 Oracle 伺服器上建立名為 "c： \\ \bfiles" 的目錄和名為 "MyFile.jpg" 的檔案。</span><span class="sxs-lookup"><span data-stu-id="59724-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59724-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59724-124">See also</span></span>

- [<span data-ttu-id="59724-125">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="59724-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- <span data-ttu-id="59724-126">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="59724-126">[ADO.NET Overview](ado-net-overview.md)</span></span>
