---
title: 單一大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 07c705b9daeeb043ef36f1e3272a3bf259a3c23e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043885"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="8aa9e-102">單一大量複製作業</span><span class="sxs-lookup"><span data-stu-id="8aa9e-102">Single Bulk Copy Operations</span></span>

<span data-ttu-id="8aa9e-103">執行 SQL Server 大量複製作業的最簡單方法是：針對資料庫執行單一作業。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="8aa9e-104">根據預設，會以隔離作業執行大量複製作業：複製作業會以非交易性方式執行，且沒有復原的機會。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>

> [!NOTE]
> <span data-ttu-id="8aa9e-105">如果需要在發生錯誤時，復原全部或部分大量複製，您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 管理的交易，或在現有交易內執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="8aa9e-106"><xref:System.Transactions>如果連接已登錄 (隱含或明確) 到**系統交易**交易, **SqlBulkCopy**也會搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>
>
> <span data-ttu-id="8aa9e-107">如需詳細資訊, 請參閱[交易和大量複製作業](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>

<span data-ttu-id="8aa9e-108">執行大量複製作業的一般步驟如下：</span><span class="sxs-lookup"><span data-stu-id="8aa9e-108">The general steps for performing a bulk copy operation are as follows:</span></span>

1. <span data-ttu-id="8aa9e-109">連接至來源伺服器，並取得要複製的資料。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="8aa9e-110">如果可從 <xref:System.Data.IDataReader> 或 <xref:System.Data.DataTable> 物件擷取資料，則資料也可來自其他來源。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>

2. <span data-ttu-id="8aa9e-111">連接到目的地伺服器 (除非您想要讓**SqlBulkCopy**為您建立連接)。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>

3. <span data-ttu-id="8aa9e-112">建立 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，設定所有必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>

4. <span data-ttu-id="8aa9e-113">設定**DestinationTableName**屬性, 以表示大量插入作業的目標資料表。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>

5. <span data-ttu-id="8aa9e-114">呼叫其中一個**WriteToServer**方法。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-114">Call one of the **WriteToServer** methods.</span></span>

6. <span data-ttu-id="8aa9e-115">(選擇性) 更新屬性, 並視需要再次呼叫**WriteToServer** 。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>

7. <span data-ttu-id="8aa9e-116">呼叫 <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>，或將大量複製作業包裝至 `Using` 陳述式內。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>

> [!CAUTION]
> <span data-ttu-id="8aa9e-117">建議來源與目標資料行的資料型別相符。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="8aa9e-118">如果資料類型不相符, **SqlBulkCopy**會嘗試使用所採用<xref:System.Data.SqlClient.SqlParameter.Value%2A>的規則, 將每個來源值轉換成目標資料類型。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="8aa9e-119">轉換可能會影響效能，亦可能導致意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="8aa9e-120">例如，`Double` 資料型別通常可轉換為 `Decimal` 資料型別，但並非始終如此。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>

## <a name="example"></a><span data-ttu-id="8aa9e-121">範例</span><span class="sxs-lookup"><span data-stu-id="8aa9e-121">Example</span></span>

<span data-ttu-id="8aa9e-122">下列主控台應用程式示範如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別來載入資料。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="8aa9e-123">在此範例中, <xref:System.Data.SqlClient.SqlDataReader>是用來將資料從 SQL Server **AdventureWorks**資料庫中的**Product**資料表複製到相同資料庫中的類似資料表。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8aa9e-124">除非您已如[大量複製範例設定](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)中所述建立工作資料表, 否則此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="8aa9e-125">這段程式碼是為了示範只使用**SqlBulkCopy**的語法而提供。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="8aa9e-126">如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="8aa9e-127">使用 Transact-SQL 及命令類別來執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="8aa9e-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>

<span data-ttu-id="8aa9e-128">下列範例說明如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法執行 BULK INSERT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>

> [!NOTE]
> <span data-ttu-id="8aa9e-129">資料來源的檔案路徑是與伺服器相對的。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="8aa9e-130">伺服器處理序必須存取該路徑，才能順利完成大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="8aa9e-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a><span data-ttu-id="8aa9e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aa9e-131">See also</span></span>

- [<span data-ttu-id="8aa9e-132">在 SQL Server 中執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="8aa9e-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="8aa9e-133">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8aa9e-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
