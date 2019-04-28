---
title: 在 SQL Server 中執行大量複製作業
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 086b3b997cf0915be7cfa603a651eb412d52e985
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878640"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="fdbc2-102">在 SQL Server 中執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="fdbc2-103">Microsoft SQL Server 包含名為的常用命令列公用程式**bcp**的快速大量複製到資料表或檢視 SQL Server 資料庫中的大型檔案。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="fdbc2-104"><xref:System.Data.SqlClient.SqlBulkCopy> 類別可讓您撰寫會提供類似功能的 Managed 程式碼方案。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="fdbc2-105">還可採用其他方式將資料載入 SQL Server 資料表 (例如，INSERT 陳述式)，但 <xref:System.Data.SqlClient.SqlBulkCopy> 的效能優勢明顯高於它們。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="fdbc2-106"><xref:System.Data.SqlClient.SqlBulkCopy> 類別可用於僅將資料寫入 SQL Server 資料表。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="fdbc2-107">但是資料來源不僅限於 SQL Server；可使用任何資料來源，只要該資料可載入 <xref:System.Data.DataTable> 執行個體，或可使用 <xref:System.Data.IDataReader> 執行個體進行讀取。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="fdbc2-108">使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，您可以執行：</span><span class="sxs-lookup"><span data-stu-id="fdbc2-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="fdbc2-109">單一大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="fdbc2-110">多項大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="fdbc2-111">在交易內的大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdbc2-112">使用.NET Framework 1.1 或更早版本時 (不支援<xref:System.Data.SqlClient.SqlBulkCopy>類別)，您可以執行 SQL Server TRANSACT-SQL **BULK INSERT**陳述式使用<xref:System.Data.SqlClient.SqlCommand>物件。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdbc2-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="fdbc2-113">In This Section</span></span>  
 [<span data-ttu-id="fdbc2-114">大量複製範例設定</span><span class="sxs-lookup"><span data-stu-id="fdbc2-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="fdbc2-115">說明大量複製範例中使用的資料表，並提供用於在 AdventureWorks 資料庫中建立資料表的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="fdbc2-116">單一大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="fdbc2-117">說明如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別將資料單一大量複製到 SQL Server 的執行個體中，以及如何使用 Transact-SQL 陳述式及 <xref:System.Data.SqlClient.SqlCommand> 類別執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="fdbc2-118">多項大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="fdbc2-119">說明如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，執行資料到 SQL Server 執行個體的多項大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="fdbc2-120">異動和大量複製作業</span><span class="sxs-lookup"><span data-stu-id="fdbc2-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="fdbc2-121">說明如何在異動內執行大量複製作業，包含如何認可或復原異動。</span><span class="sxs-lookup"><span data-stu-id="fdbc2-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbc2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdbc2-122">See also</span></span>

- [<span data-ttu-id="fdbc2-123">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fdbc2-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="fdbc2-124">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="fdbc2-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
