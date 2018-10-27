---
title: FILESTREAM 資料
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 843aa890ba80ab2816af0726170eacb77f419d50
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047978"
---
# <a name="filestream-data"></a><span data-ttu-id="ee670-102">FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="ee670-102">FILESTREAM Data</span></span>
<span data-ttu-id="ee670-103">FILESTREAM 儲存體屬性適用於儲存在 varbinary(max) 資料行中的二進位 (BLOB) 資料。</span><span class="sxs-lookup"><span data-stu-id="ee670-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="ee670-104">在引進 FILESTREAM 之前，儲存二進位資料需要特殊處理。</span><span class="sxs-lookup"><span data-stu-id="ee670-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="ee670-105">文字文件、影像和視訊等非結構化資料通常會儲存在資料庫外部，因而難以管理。</span><span class="sxs-lookup"><span data-stu-id="ee670-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee670-106">您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能使用 SqlClient 來處理 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="ee670-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="ee670-107">針對 varbinary(max) 資料行指定 FILESTREAM 屬性會導致 SQL Server 將資料儲存在本機 NTFS 檔案系統上，而非資料庫檔案中。</span><span class="sxs-lookup"><span data-stu-id="ee670-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="ee670-108">雖然系統會以不同的方式儲存資料，但是您仍可使用支援搭配儲存在資料庫中之 varbinary(max) 資料的相同 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 陳述式 (Statement)。</span><span class="sxs-lookup"><span data-stu-id="ee670-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="ee670-109">FILESTREAM 的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="ee670-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="ee670-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server <xref:System.Data.SqlClient>、 讀取和寫入 FILESTREAM 資料使用的支援<xref:System.Data.SqlTypes.SqlFileStream>類別中定義<xref:System.Data.SqlTypes>命名空間。</span><span class="sxs-lookup"><span data-stu-id="ee670-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="ee670-111">`SqlFileStream` 繼承自 <xref:System.IO.Stream> 類別，可提供讀取和寫入資料流的方法。</span><span class="sxs-lookup"><span data-stu-id="ee670-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="ee670-112">讀取資料流會將資料從資料流傳送至資料結構中，例如位元組的陣列。</span><span class="sxs-lookup"><span data-stu-id="ee670-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="ee670-113">寫入則會將資料從資料結構傳送至資料流中。</span><span class="sxs-lookup"><span data-stu-id="ee670-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-sql-server-table"></a><span data-ttu-id="ee670-114">建立 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="ee670-114">Creating the SQL Server Table</span></span>  
 <span data-ttu-id="ee670-115">下列 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 陳述式會建立名為 employees 的資料表並插入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ee670-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="ee670-116">一旦您啟用了 FILESTREAM 儲存體之後，就可以使用這份資料表搭配後面的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="ee670-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="ee670-117">SQL Server 線上叢書 》 中的資源連結位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ee670-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
```  
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="ee670-118">範例：讀取、覆寫和插入 FILESTREAM 資料</span><span class="sxs-lookup"><span data-stu-id="ee670-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="ee670-119">下列範例將示範如何從 FILESTREAM 中讀取資料。</span><span class="sxs-lookup"><span data-stu-id="ee670-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="ee670-120">這段程式碼會取得檔案的邏輯路徑，並將 `FileAccess` 設定為 `Read` 而且將 `FileOptions` 設定為 `SequentialScan`。</span><span class="sxs-lookup"><span data-stu-id="ee670-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ee670-121">然後，程式碼會將位元組從 SqlFileStream 讀入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="ee670-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="ee670-122">接著，這些位元組會寫入主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="ee670-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="ee670-123">範例也會示範如何將資料寫入會覆寫所有現有資料的 FILESTREAM 中。</span><span class="sxs-lookup"><span data-stu-id="ee670-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="ee670-124">這段程式碼會取得檔案的邏輯路徑並建立 `SqlFileStream`，並將 `FileAccess` 設定為 `Write` 而且將 `FileOptions` 設定為 `SequentialScan`。</span><span class="sxs-lookup"><span data-stu-id="ee670-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ee670-125">然後，單一位元組會寫入 `SqlFileStream`，並取代檔案中的任何資料。</span><span class="sxs-lookup"><span data-stu-id="ee670-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="ee670-126">範例也會示範如何使用 Seek 方法來附加資料至檔案的結尾，藉以將資料寫入 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="ee670-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="ee670-127">這段程式碼會取得檔案的邏輯路徑並建立 `SqlFileStream`，並將 `FileAccess` 設定為 `ReadWrite` 而且將 `FileOptions` 設定為 `SequentialScan`。</span><span class="sxs-lookup"><span data-stu-id="ee670-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ee670-128">然後，程式碼會使用 Seek 方法來搜尋至檔案的結尾，並將單一位元組附加至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="ee670-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
}
```  
  
 <span data-ttu-id="ee670-129">如需其他範例，請參閱[如何儲存和擷取至檔案資料流資料行的二進位資料](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)。</span><span class="sxs-lookup"><span data-stu-id="ee670-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="ee670-130">SQL Server 線上叢書中的資源</span><span class="sxs-lookup"><span data-stu-id="ee670-130">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="ee670-131">FILESTREAM 的完整文件位於 SQL Server 線上叢書 》 中的下列各節。</span><span class="sxs-lookup"><span data-stu-id="ee670-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="ee670-132">主題</span><span class="sxs-lookup"><span data-stu-id="ee670-132">Topic</span></span>|<span data-ttu-id="ee670-133">描述</span><span class="sxs-lookup"><span data-stu-id="ee670-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ee670-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee670-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="ee670-135">描述使用 FILESTREAM 儲存體的時機，以及它如何整合 SQL Server Database Engine 與 NTFS 檔案系統。</span><span class="sxs-lookup"><span data-stu-id="ee670-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|[<span data-ttu-id="ee670-136">建立 FILESTREAM 資料的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="ee670-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="ee670-137">描述可用於處理 FILESTREAM 資料的 Win32 API 函式。</span><span class="sxs-lookup"><span data-stu-id="ee670-137">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|[<span data-ttu-id="ee670-138">FILESTREAM 和其他 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="ee670-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="ee670-139">針對使用 FILESTREAM 資料搭配其他 SQL Server 功能提供相關的考量、指導方針和限制。</span><span class="sxs-lookup"><span data-stu-id="ee670-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee670-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee670-140">See Also</span></span>  
 [<span data-ttu-id="ee670-141">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee670-141">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="ee670-142">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="ee670-142">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ee670-143">程式碼存取安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee670-143">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="ee670-144">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="ee670-144">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="ee670-145">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="ee670-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
