---
title: SQL Server Compact 和 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792543"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="b83f4-102">SQL Server Compact 和 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b83f4-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="b83f4-103">SQL Server Compact 是隨 Visual Studio 一起安裝的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="b83f4-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="b83f4-104">如需詳細資訊，請參閱[使用 SQL Server Compact （Visual Studio）](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))。</span><span class="sxs-lookup"><span data-stu-id="b83f4-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="b83f4-105">本主題概述使用方式、設定、功能集和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援範圍中的主要差異。</span><span class="sxs-lookup"><span data-stu-id="b83f4-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="b83f4-106">有關 LINQ to SQL 的 SQL Server Compact 特性</span><span class="sxs-lookup"><span data-stu-id="b83f4-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="b83f4-107">根據預設，SQL Server Compact 會針對所有 Visual Studio 版本進行安裝，因此可在開發電腦上使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，以用於。</span><span class="sxs-lookup"><span data-stu-id="b83f4-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="b83f4-108">但是，部署使用 SQL Server Compact 且[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]與 SQL Server 應用程式不同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b83f4-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="b83f4-109">SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。</span><span class="sxs-lookup"><span data-stu-id="b83f4-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="b83f4-110">並注意下列特性：</span><span class="sxs-lookup"><span data-stu-id="b83f4-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="b83f4-111">SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="b83f4-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="b83f4-112">SQL Server Compact 在與用戶端應用程式相同的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="b83f4-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="b83f4-113">因此，與 SQL Server Compact 通訊的效率會明顯高於與 SQL Server 通訊。</span><span class="sxs-lookup"><span data-stu-id="b83f4-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="b83f4-114">另一方面，SQL Server Compact 需要受控和非受控碼之間的互通性，以及其附隨的費用。</span><span class="sxs-lookup"><span data-stu-id="b83f4-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="b83f4-115">SQL Server Compact DLL 的大小很小。</span><span class="sxs-lookup"><span data-stu-id="b83f4-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="b83f4-116">這項功能可縮減應用程式整體大小。</span><span class="sxs-lookup"><span data-stu-id="b83f4-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="b83f4-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="b83f4-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="b83f4-118">物件關聯式設計工具不支援 SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="b83f4-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="b83f4-119">功能集</span><span class="sxs-lookup"><span data-stu-id="b83f4-119">Feature Set</span></span>  
 <span data-ttu-id="b83f4-120">SQL Server Compact 功能集比 SQL Server 的功能集簡單許多，可能會影響[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]應用程式：</span><span class="sxs-lookup"><span data-stu-id="b83f4-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="b83f4-121">SQL Server Compact 不支援預存程序或檢視。</span><span class="sxs-lookup"><span data-stu-id="b83f4-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="b83f4-122">SQL Server Compact 僅支援部分的資料類型和 SQL 函式。</span><span class="sxs-lookup"><span data-stu-id="b83f4-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="b83f4-123">SQL Server Compact 僅支援部分的 SQL 建構。</span><span class="sxs-lookup"><span data-stu-id="b83f4-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="b83f4-124">SQL Server Compact 僅提供最簡單的最佳化工具。</span><span class="sxs-lookup"><span data-stu-id="b83f4-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="b83f4-125">有些查詢可能會超時。</span><span class="sxs-lookup"><span data-stu-id="b83f4-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="b83f4-126">SQL Server Compact 不支援部分信任。</span><span class="sxs-lookup"><span data-stu-id="b83f4-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b83f4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b83f4-127">See also</span></span>

- [<span data-ttu-id="b83f4-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="b83f4-128">Reference</span></span>](reference.md)
