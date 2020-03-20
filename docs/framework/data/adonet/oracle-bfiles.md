---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149436"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="23f6e-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="23f6e-102">Oracle BFILEs</span></span>
<span data-ttu-id="23f6e-103">Oracle 的 .NET Framework 資料提供者包括 <xref:System.Data.OracleClient.OracleBFile> 類別，可用來與 Oracle <xref:System.Data.OracleClient.OracleType.BFile> 資料型別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="23f6e-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="23f6e-104">Oracle **BFILE**資料類型是 Oracle **LOB**資料類型，其中包含對最大大小為 4 GB 的二進位資料的引用。</span><span class="sxs-lookup"><span data-stu-id="23f6e-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="23f6e-105">Oracle **BFILE**與其他 Oracle **LOB**資料類型不同，其資料存儲在作業系統中的物理檔中，而不是存儲在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="23f6e-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="23f6e-106">請注意 **，BFILE**資料類型提供對資料的唯讀訪問。</span><span class="sxs-lookup"><span data-stu-id="23f6e-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="23f6e-107">**BFILE**資料類型區別于**LOB**資料類型的其他特徵是：</span><span class="sxs-lookup"><span data-stu-id="23f6e-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="23f6e-108">包含非結構化資料。</span><span class="sxs-lookup"><span data-stu-id="23f6e-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="23f6e-109">支援伺服器端區塊。</span><span class="sxs-lookup"><span data-stu-id="23f6e-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="23f6e-110">使用參考複製語意。</span><span class="sxs-lookup"><span data-stu-id="23f6e-110">Uses reference copy semantics.</span></span> <span data-ttu-id="23f6e-111">例如，如果對**BFILE**執行複製操作，則僅複製**BFILE**定位器（即對檔的引用）。</span><span class="sxs-lookup"><span data-stu-id="23f6e-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="23f6e-112">而不會複製檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="23f6e-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="23f6e-113">**BFILE**資料類型應用於引用大尺寸的 LOB，因此，在資料庫中存儲起來不可行。</span><span class="sxs-lookup"><span data-stu-id="23f6e-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="23f6e-114">與**LOB**資料類型相比，使用**BFILE**資料類型時，涉及更多的用戶端、伺服器和通信開銷。</span><span class="sxs-lookup"><span data-stu-id="23f6e-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="23f6e-115">如果您只需要獲取少量資料，則訪問**BFILE**會更有效。</span><span class="sxs-lookup"><span data-stu-id="23f6e-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="23f6e-116">如果您需要取得整個物件，則存取常駐於資料庫的 LOB 會更有效率。</span><span class="sxs-lookup"><span data-stu-id="23f6e-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="23f6e-117">每個非 Null **OracleBFile**物件都與定義基礎物理檔位置的兩個實體相關聯：</span><span class="sxs-lookup"><span data-stu-id="23f6e-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="23f6e-118">Oracle DIRECTORY 物件 (檔案系統中目錄的資料庫別名) 及</span><span class="sxs-lookup"><span data-stu-id="23f6e-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="23f6e-119">基礎實體檔案的檔名 (位於與 DIRECTORY 物件相關聯的目錄中)。</span><span class="sxs-lookup"><span data-stu-id="23f6e-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23f6e-120">範例</span><span class="sxs-lookup"><span data-stu-id="23f6e-120">Example</span></span>  
 <span data-ttu-id="23f6e-121">以下 C# 示例演示如何在 Oracle 表中創建**BFILE，** 然後以**OracleBFile**物件的形式檢索它。</span><span class="sxs-lookup"><span data-stu-id="23f6e-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="23f6e-122">該示例演示了使用<xref:System.Data.OracleClient.OracleDataReader>物件和**OracleBFile** **查找**和**讀取**方法。</span><span class="sxs-lookup"><span data-stu-id="23f6e-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="23f6e-123">請注意，要使用此示例，必須首先在 Oracle 伺服器上創建名為"c：\\\bfile"的目錄和名為"MyFile.jpg"的檔。</span><span class="sxs-lookup"><span data-stu-id="23f6e-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23f6e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23f6e-124">See also</span></span>

- [<span data-ttu-id="23f6e-125">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="23f6e-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- <span data-ttu-id="23f6e-126">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="23f6e-126">[ADO.NET Overview](ado-net-overview.md)</span></span>
