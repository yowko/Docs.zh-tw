---
title: 大量複製範例設定
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: ac09ed85315aee7c6b29952916088ebe6e301eb9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794427"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="bd3b5-102">大量複製範例設定</span><span class="sxs-lookup"><span data-stu-id="bd3b5-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="bd3b5-103"><xref:System.Data.SqlClient.SqlBulkCopy> 類別可用於僅將資料寫入 SQL Server 資料表。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="bd3b5-104">本主題所顯示的程式碼範例會使用 SQL Server 範例資料庫**AdventureWorks**。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="bd3b5-105">為了避免變更現有資料表的程式碼範例，請將資料寫入您必須先建立的資料表中。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="bd3b5-106">**BulkCopyDemoMatchingColumns**和**BulkCopyDemoDifferentColumns**資料表都是以**AdventureWorks** **生產產品**資料表為基礎。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="bd3b5-107">在使用這些資料表的程式碼範例中，會將資料從**Products**資料表加入至這些範例資料表的其中一個。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="bd3b5-108">當範例示範如何將資料行從來源資料對應至目的地資料表時，會使用**BulkCopyDemoDifferentColumns**資料表。**BulkCopyDemoMatchingColumns**用於大部分的其他範例。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="bd3b5-109">幾個程式碼範例會示範如何使用一個 <xref:System.Data.SqlClient.SqlBulkCopy> 類別來寫入多個資料表。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="bd3b5-110">在這些範例中，會使用**BulkCopyDemoOrderHeader**和**BulkCopyDemoOrderDetail**資料表做為目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="bd3b5-111">這些資料表是以**AdventureWorks**中的**SalesOrderHeader**和**SalesOrderDetail**資料表為基礎。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd3b5-112">提供的**SqlBulkCopy**程式碼範例僅示範使用**SqlBulkCopy**的語法。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="bd3b5-113">如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="bd3b5-114">資料表設定</span><span class="sxs-lookup"><span data-stu-id="bd3b5-114">Table Setup</span></span>  
 <span data-ttu-id="bd3b5-115">若要建立讓程式碼範例正確執行所需的資料表，您必須在 SQL Server 資料庫中執行下列 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bd3b5-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd3b5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd3b5-116">See also</span></span>

- [<span data-ttu-id="bd3b5-117">在 SQL Server 中執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="bd3b5-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="bd3b5-118">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="bd3b5-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
