---
title: 在 SQL Server 中執行大量複製作業
description: 瞭解如何使用 SqlBulkCopy 類別來撰寫 managed 程式碼解決方案，將大型檔案大量複製到 SQL Server 資料庫中的資料表或 views。
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286516"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="1d58a-103">在 SQL Server 中執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-103">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="1d58a-104">Microsoft SQL Server 包含名為 **bcp** 的常用命令列公用程式，用於將大型檔案快速大量複製到 SQL Server 資料庫中的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="1d58a-104">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="1d58a-105"><xref:System.Data.SqlClient.SqlBulkCopy> 類別可讓您撰寫受控程式碼解決方案來提供類似功能。</span><span class="sxs-lookup"><span data-stu-id="1d58a-105">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="1d58a-106">還有其他方法可以將資料載入 SQL Server 資料表 (例如 INSERT 陳述式)，但 <xref:System.Data.SqlClient.SqlBulkCopy> 提供顯著超越其他方法的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="1d58a-106">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="1d58a-107"><xref:System.Data.SqlClient.SqlBulkCopy> 類別只能用來將資料寫入到 SQL Server 資料表。</span><span class="sxs-lookup"><span data-stu-id="1d58a-107">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="1d58a-108">但是資料來源不僅限於 SQL Server；可使用任何資料來源，只要該資料可載入 <xref:System.Data.DataTable> 執行個體，或可使用 <xref:System.Data.IDataReader> 執行個體進行讀取。</span><span class="sxs-lookup"><span data-stu-id="1d58a-108">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="1d58a-109">使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，您可以執行：</span><span class="sxs-lookup"><span data-stu-id="1d58a-109">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="1d58a-110">單一大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-110">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="1d58a-111">多項大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-111">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="1d58a-112">交易內的大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-112">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d58a-113">當使用 .NET Framework 1.1 版或更早版本 (不支援 <xref:System.Data.SqlClient.SqlBulkCopy> 類別) 時，您可使用 <xref:System.Data.SqlClient.SqlCommand> 物件執行 SQL Server Transact-SQL **BULK INSERT** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1d58a-113">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d58a-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="1d58a-114">In This Section</span></span>  
 [<span data-ttu-id="1d58a-115">大量複製範例設定</span><span class="sxs-lookup"><span data-stu-id="1d58a-115">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="1d58a-116">描述大量複製範例中所使用的資料表，並提供可用來在 AdventureWorks 資料庫中建立資料表的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1d58a-116">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="1d58a-117">單一大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-117">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="1d58a-118">描述如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，在 SQL Server 的執行個體中單一大量複製資料，以及如何使用 Transact-SQL 陳述式和 <xref:System.Data.SqlClient.SqlCommand> 類別來執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="1d58a-118">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="1d58a-119">多個大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-119">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="1d58a-120">描述如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別，在 SQL Server 的執行個體中執行資料的多個大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="1d58a-120">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="1d58a-121">交易和大量複製作業</span><span class="sxs-lookup"><span data-stu-id="1d58a-121">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="1d58a-122">描述如何在交易內執行大量複製作業，包括如何認可或復原交易。</span><span class="sxs-lookup"><span data-stu-id="1d58a-122">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d58a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d58a-123">See also</span></span>

- <span data-ttu-id="1d58a-124">[SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1d58a-124">[SQL Server and ADO.NET](index.md)</span></span>
- <span data-ttu-id="1d58a-125">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="1d58a-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>
