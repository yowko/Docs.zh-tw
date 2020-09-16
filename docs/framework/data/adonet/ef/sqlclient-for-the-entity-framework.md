---
title: 適用於 Entity Framework 的 SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: e9bf1014bdbc14b854d3b37d488d75878d1a3473
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552241"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="a0b27-102">適用於 Entity Framework 的 SqlClient</span><span class="sxs-lookup"><span data-stu-id="a0b27-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="a0b27-103">本節將描述可讓 Entity Framework 透過 Microsoft SQL Server 運作的 .NET Framework Data Provider for SQL Server (SqlClient)。</span><span class="sxs-lookup"><span data-stu-id="a0b27-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="a0b27-104">Provider 結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="a0b27-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="a0b27-105">在存放結構定義語言 (SSDL) 中，`Provider` 是 `Schema` 項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b27-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="a0b27-106">若要使用 SqlClient，請將字串 "System.Data.SqlClient" 指派給 `Provider` 項目的 `Schema` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b27-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="a0b27-107">ProviderManifestToken 結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="a0b27-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="a0b27-108">在 SSDL 中，`ProviderManifestToken` 是 `Schema` 項目的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b27-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="a0b27-109">這個語彙基元 (Token) 是用來載入提供者資訊清單以供離線案例使用。</span><span class="sxs-lookup"><span data-stu-id="a0b27-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="a0b27-110">如需屬性的詳細資訊 `ProviderManifestToken` ，請參閱 [ (SSDL) 的架構元素 ](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl)。</span><span class="sxs-lookup"><span data-stu-id="a0b27-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="a0b27-111">SqlClient 可當做不同 SQL Server 版本的資料提供者使用。</span><span class="sxs-lookup"><span data-stu-id="a0b27-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="a0b27-112">這些版本具有不同的功能。</span><span class="sxs-lookup"><span data-stu-id="a0b27-112">These versions have different capabilities.</span></span> <span data-ttu-id="a0b27-113">例如，SQL Server 2000 不支援 `varchar(max)` `nvarchar(max)` SQL Server 2005 引進的和類型。</span><span class="sxs-lookup"><span data-stu-id="a0b27-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="a0b27-114">SqlClient 會針對不同的 SQL Server 版本，產生並接受下列提供者資訊清單語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a0b27-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="a0b27-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="a0b27-115">SQL Server 2000</span></span>|<span data-ttu-id="a0b27-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="a0b27-116">SQL Server 2005</span></span>|<span data-ttu-id="a0b27-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="a0b27-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="a0b27-118">2000</span><span class="sxs-lookup"><span data-stu-id="a0b27-118">2000</span></span>|<span data-ttu-id="a0b27-119">2005</span><span class="sxs-lookup"><span data-stu-id="a0b27-119">2005</span></span>|<span data-ttu-id="a0b27-120">2008</span><span class="sxs-lookup"><span data-stu-id="a0b27-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a0b27-121">從 Visual Studio 2010 開始， [ADO.NET 實體資料模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) 不支援 SQL Server 2000。</span><span class="sxs-lookup"><span data-stu-id="a0b27-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="a0b27-122">提供者命名空間名稱</span><span class="sxs-lookup"><span data-stu-id="a0b27-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="a0b27-123">所有提供者都必須指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="a0b27-123">All providers must specify a namespace.</span></span> <span data-ttu-id="a0b27-124">這個屬性會告知 Entity Framework 此提供者對特定建構 (例如型別和函式) 所使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="a0b27-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="a0b27-125">SqlClient 提供者資訊清單的命名空間是 `SqlServer`。</span><span class="sxs-lookup"><span data-stu-id="a0b27-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="a0b27-126">如需命名空間的詳細資訊，請參閱 [命名空間](./language-reference/namespaces-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b27-126">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="a0b27-127">類型</span><span class="sxs-lookup"><span data-stu-id="a0b27-127">Types</span></span>  
 <span data-ttu-id="a0b27-128">適用於 Entity Framework 的 SqlClient 提供者會提供概念模型類型和 SQL Server 型別之間的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="a0b27-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="a0b27-129">如需詳細資訊，請參閱 [Entity FrameworkTypes 的 SqlClient](sqlclient-for-ef-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b27-129">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="a0b27-130">函式</span><span class="sxs-lookup"><span data-stu-id="a0b27-130">Functions</span></span>  
 <span data-ttu-id="a0b27-131">Entity Framework 的 SqlClient 提供者會定義提供者所支援的函式清單。</span><span class="sxs-lookup"><span data-stu-id="a0b27-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="a0b27-132">如需支援的函式清單，請參閱 Entity Framework 函式的 [SqlClient](sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b27-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0b27-133">本節內容</span><span class="sxs-lookup"><span data-stu-id="a0b27-133">In This Section</span></span>  
 [<span data-ttu-id="a0b27-134">適用於 Entity Framework 的 SqlClient 函式</span><span class="sxs-lookup"><span data-stu-id="a0b27-134">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="a0b27-135">適用於 Entity Framework 之 SqlClient 的類型</span><span class="sxs-lookup"><span data-stu-id="a0b27-135">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="a0b27-136">適用於 Entity Framework 的 SqlClient 已知問題</span><span class="sxs-lookup"><span data-stu-id="a0b27-136">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="a0b27-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b27-137">See also</span></span>

- [<span data-ttu-id="a0b27-138">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="a0b27-138">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="a0b27-139">語言參考</span><span class="sxs-lookup"><span data-stu-id="a0b27-139">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="a0b27-140">SqlClient Provider for Entity Framework 的已知問題</span><span class="sxs-lookup"><span data-stu-id="a0b27-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
