---
title: SQL Server Compact 和 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: bdd1237a8eac1c278e7704f3fbf0ae8b1deeff42
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541359"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="4b71b-102">SQL Server Compact 和 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4b71b-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="4b71b-103">SQL Server Compact 是隨 Visual Studio 安裝的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="4b71b-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="4b71b-104">如需詳細資訊，請參閱 [使用 SQL Server Compact (Visual Studio) ](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))。</span><span class="sxs-lookup"><span data-stu-id="4b71b-104">For more information, see [Using SQL Server Compact (Visual Studio)](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="4b71b-105">本主題將概述使用方式、設定、功能集和支援範圍的主要差異 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b71b-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="4b71b-106">有關 LINQ to SQL 的 SQL Server Compact 特性</span><span class="sxs-lookup"><span data-stu-id="4b71b-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="4b71b-107">根據預設，會針對所有 Visual Studio 版本安裝 SQL Server Compact，因此可在開發電腦上使用，以搭配使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b71b-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="4b71b-108">但是，部署使用 SQL Server Compact 的應用程式，以及與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server 應用程式不同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b71b-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="4b71b-109">SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。</span><span class="sxs-lookup"><span data-stu-id="4b71b-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="4b71b-110">並注意下列特性：</span><span class="sxs-lookup"><span data-stu-id="4b71b-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="4b71b-111">SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="4b71b-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="4b71b-112">SQL Server Compact 會在與用戶端應用程式相同的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="4b71b-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="4b71b-113">因此，與 SQL Server Compact 的通訊效率可能會比使用 SQL Server 更高。</span><span class="sxs-lookup"><span data-stu-id="4b71b-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="4b71b-114">另一方面，SQL Server Compact 一定需要 Managed 程式碼和 Unmanaged 程式碼與其附帶成本之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="4b71b-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="4b71b-115">SQL Server Compact DLL 不大。</span><span class="sxs-lookup"><span data-stu-id="4b71b-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="4b71b-116">這項功能可縮減應用程式整體大小。</span><span class="sxs-lookup"><span data-stu-id="4b71b-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="4b71b-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="4b71b-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="4b71b-118">物件關聯式設計工具不支援 SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="4b71b-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="4b71b-119">功能集</span><span class="sxs-lookup"><span data-stu-id="4b71b-119">Feature Set</span></span>  
 <span data-ttu-id="4b71b-120">SQL Server Compact 功能集比 SQL Server 的功能集簡單許多，可能會影響 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式：</span><span class="sxs-lookup"><span data-stu-id="4b71b-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="4b71b-121">SQL Server Compact 不支援預存程序或檢視。</span><span class="sxs-lookup"><span data-stu-id="4b71b-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="4b71b-122">SQL Server Compact 僅支援部分的資料類型和 SQL 函式。</span><span class="sxs-lookup"><span data-stu-id="4b71b-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="4b71b-123">SQL Server Compact 僅支援部分的 SQL 建構。</span><span class="sxs-lookup"><span data-stu-id="4b71b-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="4b71b-124">SQL Server Compact 僅提供最簡單的最佳化工具。</span><span class="sxs-lookup"><span data-stu-id="4b71b-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="4b71b-125">因此有些查詢可能會逾時。</span><span class="sxs-lookup"><span data-stu-id="4b71b-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="4b71b-126">SQL Server Compact 不支援部分信任。</span><span class="sxs-lookup"><span data-stu-id="4b71b-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b71b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b71b-127">See also</span></span>

- [<span data-ttu-id="4b71b-128">參考</span><span class="sxs-lookup"><span data-stu-id="4b71b-128">Reference</span></span>](reference.md)
