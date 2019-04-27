---
title: SQL 產生
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 108a68f74849c7fa1418775c2a37db06d9d947ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879147"
---
# <a name="sql-generation"></a><span data-ttu-id="2f945-102">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="2f945-102">SQL Generation</span></span>
<span data-ttu-id="2f945-103">當您為 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 撰寫提供者時，您必須將 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 命令樹轉譯成特定資料庫可以了解的 SQL，例如 SQL Server 的 Transact-SQL 或 Oracle 的 PL/SQL。</span><span class="sxs-lookup"><span data-stu-id="2f945-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="2f945-104">在本章節中，您將會學習如何為 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 提供者開發 SQL 產生元件 (適用於 SELECT 查詢)。</span><span class="sxs-lookup"><span data-stu-id="2f945-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="2f945-105">如需插入資訊，更新和刪除查詢，請參閱[修改 SQL 產生](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)。</span><span class="sxs-lookup"><span data-stu-id="2f945-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="2f945-106">若要了解本章節，您應該要熟悉 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 及 ADO.NET 提供者模型。</span><span class="sxs-lookup"><span data-stu-id="2f945-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="2f945-107">您也應該了解命令樹和 <xref:System.Data.Common.CommandTrees.DbExpression>。</span><span class="sxs-lookup"><span data-stu-id="2f945-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="2f945-108">SQL 產生模組的角色</span><span class="sxs-lookup"><span data-stu-id="2f945-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="2f945-109">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 提供者的 SQL 產生模組會將給定的查詢命令樹轉譯成單一 SQL SELECT 陳述式，此陳述式是以 SQL:1999 相容的資料庫為目標。</span><span class="sxs-lookup"><span data-stu-id="2f945-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="2f945-110">產生的 SQL 應該盡量擁有少一點的巢狀查詢。</span><span class="sxs-lookup"><span data-stu-id="2f945-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="2f945-111">SQL 產生模組不應該簡化查詢命令樹的輸出。</span><span class="sxs-lookup"><span data-stu-id="2f945-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="2f945-112">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 將會進行這項處理，例如藉由除去聯結及摺疊連續的篩選節點。</span><span class="sxs-lookup"><span data-stu-id="2f945-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="2f945-113"><xref:System.Data.Common.DbProviderServices> 類別是存取 SQL 產生層的起點，可將命令樹轉換成 <xref:System.Data.Common.DbCommand>。</span><span class="sxs-lookup"><span data-stu-id="2f945-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f945-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="2f945-114">In This Section</span></span>  
 [<span data-ttu-id="2f945-115">命令樹的形狀</span><span class="sxs-lookup"><span data-stu-id="2f945-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="2f945-116">從命令樹產生 SQL - 最佳做法</span><span class="sxs-lookup"><span data-stu-id="2f945-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="2f945-117">範例提供者中的 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="2f945-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f945-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f945-118">See also</span></span>

- [<span data-ttu-id="2f945-119">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="2f945-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
