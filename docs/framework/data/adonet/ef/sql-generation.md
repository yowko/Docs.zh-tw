---
title: SQL 產生
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854363"
---
# <a name="sql-generation"></a><span data-ttu-id="9da3f-102">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="9da3f-102">SQL Generation</span></span>
<span data-ttu-id="9da3f-103">當您撰寫 Entity Framework 的提供者時，您必須將 Entity Framework 的命令樹轉譯成特定資料庫可瞭解的 SQL，例如適用于 SQL Server 的 Transact-sql 或 Oracle 的 PL/SQL。</span><span class="sxs-lookup"><span data-stu-id="9da3f-103">When you write a provider for the Entity Framework, you must translate Entity Framework command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="9da3f-104">在本節中，您將瞭解如何為 Entity Framework 提供者開發 SQL 世代元件（適用于 SELECT 查詢）。</span><span class="sxs-lookup"><span data-stu-id="9da3f-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an Entity Framework provider.</span></span> <span data-ttu-id="9da3f-105">如需插入、更新和刪除查詢的詳細資訊，請參閱[修改 SQL 產生](modification-sql-generation.md)。</span><span class="sxs-lookup"><span data-stu-id="9da3f-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="9da3f-106">若要瞭解這一節，您應該熟悉 Entity Framework 和 ADO.NET 提供者模型。</span><span class="sxs-lookup"><span data-stu-id="9da3f-106">To understand this section, you should be familiar with the Entity Framework and the ADO.NET Provider Model.</span></span> <span data-ttu-id="9da3f-107">您也應該了解命令樹和 <xref:System.Data.Common.CommandTrees.DbExpression>。</span><span class="sxs-lookup"><span data-stu-id="9da3f-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="9da3f-108">SQL 產生模組的角色</span><span class="sxs-lookup"><span data-stu-id="9da3f-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="9da3f-109">Entity Framework 提供者的 SQL 產生模組會將指定的查詢命令樹轉譯成以 SQL：1999相容資料庫為目標的單一 SQL SELECT 語句。</span><span class="sxs-lookup"><span data-stu-id="9da3f-109">The SQL generation module of an Entity Framework provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="9da3f-110">產生的 SQL 應該盡量擁有少一點的巢狀查詢。</span><span class="sxs-lookup"><span data-stu-id="9da3f-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="9da3f-111">SQL 產生模組不應該簡化查詢命令樹的輸出。</span><span class="sxs-lookup"><span data-stu-id="9da3f-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="9da3f-112">Entity Framework 將會執行這項操作，例如，藉由排除聯結和折迭連續的篩選節點。</span><span class="sxs-lookup"><span data-stu-id="9da3f-112">The Entity Framework will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="9da3f-113"><xref:System.Data.Common.DbProviderServices> 類別是存取 SQL 產生層的起點，可將命令樹轉換成 <xref:System.Data.Common.DbCommand>。</span><span class="sxs-lookup"><span data-stu-id="9da3f-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9da3f-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="9da3f-114">In This Section</span></span>  
 [<span data-ttu-id="9da3f-115">命令樹的形狀</span><span class="sxs-lookup"><span data-stu-id="9da3f-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="9da3f-116">從命令樹產生 SQL - 最佳做法</span><span class="sxs-lookup"><span data-stu-id="9da3f-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="9da3f-117">範例提供者中的 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="9da3f-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="9da3f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9da3f-118">See also</span></span>

- [<span data-ttu-id="9da3f-119">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="9da3f-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
