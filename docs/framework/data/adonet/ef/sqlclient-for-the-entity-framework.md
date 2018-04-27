---
title: 適用於 Entity Framework 的 SqlClient
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 2801ad445be073f2cd4725d04a0c731e8bfcdd1b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="d083d-102">適用於 Entity Framework 的 SqlClient</span><span class="sxs-lookup"><span data-stu-id="d083d-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="d083d-103">本節將描述可讓 Entity Framework 透過 Microsoft SQL Server 運作的 .NET Framework Data Provider for SQL Server (SqlClient)。</span><span class="sxs-lookup"><span data-stu-id="d083d-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="d083d-104">Provider 結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="d083d-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="d083d-105">在存放結構定義語言 (SSDL) 中，`Provider` 是 `Schema` 項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="d083d-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="d083d-106">若要使用 SqlClient，請將字串 "System.Data.SqlClient" 指派給 `Provider` 項目的 `Schema` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d083d-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="d083d-107">ProviderManifestToken 結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="d083d-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="d083d-108">在 SSDL 中，`ProviderManifestToken` 是 `Schema` 項目的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d083d-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="d083d-109">這個語彙基元 (Token) 是用來載入提供者資訊清單以供離線案例使用。</span><span class="sxs-lookup"><span data-stu-id="d083d-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="d083d-110">如需有關`ProviderManifestToken`屬性，請參閱[結構描述項目 (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222)。</span><span class="sxs-lookup"><span data-stu-id="d083d-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).</span></span>  
  
 <span data-ttu-id="d083d-111">SqlClient 可當做資料提供者的不同版本的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d083d-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="d083d-112">這些版本具有不同的功能。</span><span class="sxs-lookup"><span data-stu-id="d083d-112">These versions have different capabilities.</span></span> <span data-ttu-id="d083d-113">例如，[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] 不支援 `varchar(max)` 所導入的 `nvarchar(max)` 和 [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] 型別。</span><span class="sxs-lookup"><span data-stu-id="d083d-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="d083d-114">SqlClient 會針對不同的 SQL Server 版本，產生並接受下列提供者資訊清單語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d083d-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="d083d-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="d083d-115">SQL Server 2000</span></span>|<span data-ttu-id="d083d-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="d083d-116">SQL Server 2005</span></span>|<span data-ttu-id="d083d-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="d083d-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="d083d-118">2000</span><span class="sxs-lookup"><span data-stu-id="d083d-118">2000</span></span>|<span data-ttu-id="d083d-119">2005</span><span class="sxs-lookup"><span data-stu-id="d083d-119">2005</span></span>|<span data-ttu-id="d083d-120">2008</span><span class="sxs-lookup"><span data-stu-id="d083d-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d083d-121">從開始[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)]2010年[ADO.NET 實體資料模型工具](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)不支援 SQL Server 2000。</span><span class="sxs-lookup"><span data-stu-id="d083d-121">Starting with [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, the [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="d083d-122">提供者命名空間名稱</span><span class="sxs-lookup"><span data-stu-id="d083d-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="d083d-123">所有提供者都必須指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="d083d-123">All providers must specify a namespace.</span></span> <span data-ttu-id="d083d-124">這個屬性會告知 Entity Framework 此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="d083d-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="d083d-125">SqlClient 提供者資訊清單的命名空間是 `SqlServer`。</span><span class="sxs-lookup"><span data-stu-id="d083d-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="d083d-126">如需命名空間的詳細資訊，請參閱[命名空間](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="d083d-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="d083d-127">類型</span><span class="sxs-lookup"><span data-stu-id="d083d-127">Types</span></span>  
 <span data-ttu-id="d083d-128">適用於 Entity Framework 的 SqlClient 提供者會提供概念模型類型和 SQL Server 型別之間的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="d083d-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="d083d-129">如需詳細資訊，請參閱[適用於 Entity Framework 的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d083d-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="d083d-130">函式</span><span class="sxs-lookup"><span data-stu-id="d083d-130">Functions</span></span>  
 <span data-ttu-id="d083d-131">Entity Framework 的 SqlClient 提供者會定義提供者所支援的函式清單。</span><span class="sxs-lookup"><span data-stu-id="d083d-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="d083d-132">如需支援的函式的清單，請參閱[適用於 Entity Framework 函式的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="d083d-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d083d-133">本節內容</span><span class="sxs-lookup"><span data-stu-id="d083d-133">In This Section</span></span>  
 [<span data-ttu-id="d083d-134">適用於 Entity Framework 的 SqlClient 函式</span><span class="sxs-lookup"><span data-stu-id="d083d-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="d083d-135">適用於 Entity Framework 的 SqlClient 類型</span><span class="sxs-lookup"><span data-stu-id="d083d-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="d083d-136">適用於 Entity Framework 的 SqlClient 已知問題</span><span class="sxs-lookup"><span data-stu-id="d083d-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="d083d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d083d-137">See Also</span></span>  
 [<span data-ttu-id="d083d-138">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="d083d-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="d083d-139">語言參考</span><span class="sxs-lookup"><span data-stu-id="d083d-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [<span data-ttu-id="d083d-140">Entity Framework 的 SqlClient 提供者中的已知問題</span><span class="sxs-lookup"><span data-stu-id="d083d-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
