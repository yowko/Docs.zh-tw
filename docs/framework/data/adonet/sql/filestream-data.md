---
title: FILESTREAM 資料
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 87bed5dd345c240cc00b2c36aa976ec53fe63b93
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794091"
---
# <a name="filestream-data"></a>FILESTREAM 資料

FILESTREAM 儲存體屬性適用於儲存在 varbinary(max) 資料行中的二進位 (BLOB) 資料。 在引進 FILESTREAM 之前，儲存二進位資料需要特殊處理。 文字文件、影像和視訊等非結構化資料通常會儲存在資料庫外部，因而難以管理。

> [!NOTE]
> 您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能使用 SqlClient 來處理 FILESTREAM 資料。

針對 varbinary(max) 資料行指定 FILESTREAM 屬性會導致 SQL Server 將資料儲存在本機 NTFS 檔案系統上，而非資料庫檔案中。 雖然系統會以不同的方式儲存資料，但是您可以使用支援使用儲存在資料庫中之 varbinary(max) 資料的相同 Transact-SQL 陳述式 (Statement)。

## <a name="sqlclient-support-for-filestream"></a>FILESTREAM 的 SqlClient 支援

SQL Server <xref:System.Data.SqlClient>的 .NET Framework Data Provider 支援使用<xref:System.Data.SqlTypes>命名空間中定義的<xref:System.Data.SqlTypes.SqlFileStream>類別來讀取和寫入 FILESTREAM 資料。 `SqlFileStream` 繼承自 <xref:System.IO.Stream> 類別，可提供讀取和寫入資料流的方法。 讀取資料流會將資料從資料流傳送至資料結構中，例如位元組的陣列。 寫入則會將資料從資料結構傳送至資料流中。

### <a name="creating-the-sql-server-table"></a>建立 SQL Server 資料表

下列 Transact-SQL 陳述式會建立名為 employees 的資料表並插入一個資料列。 一旦您啟用了 FILESTREAM 儲存體之後，就可以使用這份資料表搭配後面的程式碼範例。 SQL Server 線上叢書中資源的連結位於本主題的結尾。

```sql
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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>範例：讀取、覆寫和插入 FILESTREAM 資料

下列範例將示範如何從 FILESTREAM 中讀取資料。 這段程式碼會取得檔案的邏輯路徑，並將 `FileAccess` 設定為 `Read` 而且將 `FileOptions` 設定為 `SequentialScan`。 然後，程式碼會將位元組從 SqlFileStream 讀入緩衝區中。 接著，這些位元組會寫入主控台視窗。

範例也會示範如何將資料寫入會覆寫所有現有資料的 FILESTREAM 中。 這段程式碼會取得檔案的邏輯路徑並建立 `SqlFileStream`，並將 `FileAccess` 設定為 `Write` 而且將 `FileOptions` 設定為 `SequentialScan`。 然後，單一位元組會寫入 `SqlFileStream`，並取代檔案中的任何資料。

範例也會示範如何使用 Seek 方法來附加資料至檔案的結尾，藉以將資料寫入 FILESTREAM。 這段程式碼會取得檔案的邏輯路徑並建立 `SqlFileStream`，並將 `FileAccess` 設定為 `ReadWrite` 而且將 `FileOptions` 設定為 `SequentialScan`。 然後，程式碼會使用 Seek 方法來搜尋至檔案的結尾，並將單一位元組附加至現有的檔案。

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
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
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

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
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

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
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

如需其他範例，請參閱[如何將二進位資料儲存和提取到檔案資料流程資料行](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str)。

## <a name="resources-in-sql-server-books-online"></a>SQL Server 線上叢書中的資源

FILESTREAM 的完整檔位於 SQL Server 線上叢書的下列各節中。

|主題|描述|
|-----------|-----------------|
|[FILESTREAM （SQL Server）](/sql/relational-databases/blob/filestream-sql-server)|描述使用 FILESTREAM 儲存體的時機，以及它如何整合 SQL Server Database Engine 與 NTFS 檔案系統。|
|[建立 FILESTREAM 資料的用戶端應用程式](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|說明用來處理 FILESTREAM 資料的 Windows API 函式。|
|[FILESTREAM 和其他 SQL Server 功能](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|針對使用 FILESTREAM 資料搭配其他 SQL Server 功能提供相關的考量、指導方針和限制。|

## <a name="see-also"></a>另請參閱

- [SQL Server 資料類型和 ADO.NET](sql-server-data-types.md)
- [在 ADO.NET 中擷取和修改資料](../retrieving-and-modifying-data.md)
- [程式碼存取安全性和 ADO.NET](../code-access-security.md)
- [SQL Server 二進位和大量數值資料](sql-server-binary-and-large-value-data.md)
- [ADO.NET 概觀](../ado-net-overview.md)
