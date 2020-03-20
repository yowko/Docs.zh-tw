---
title: 提供者資訊清單規格
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 28bae8a6e249aa1fdab3c67759c8f8575cbdaa10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149722"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="d8c24-102">提供者資訊清單規格</span><span class="sxs-lookup"><span data-stu-id="d8c24-102">Provider Manifest Specification</span></span>
<span data-ttu-id="d8c24-103">本節將討論資料存放區提供者如何支援資料存放區中的型別與函式。</span><span class="sxs-lookup"><span data-stu-id="d8c24-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="d8c24-104">雖然實體服務的運作與特定資料存放區提供者無關，不過它仍然允許資料提供者明確定義模型、對應和查詢與基礎資料存放區互動的方式。</span><span class="sxs-lookup"><span data-stu-id="d8c24-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="d8c24-105">如果沒有抽象層，實體服務的目標只能設定為特定資料存放區或資料提供者。</span><span class="sxs-lookup"><span data-stu-id="d8c24-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="d8c24-106">基礎資料庫會直接或間接支援提供者所支援的型別。</span><span class="sxs-lookup"><span data-stu-id="d8c24-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="d8c24-107">這些類型不一定是確切的存儲類型，但提供程式用於支援實體框架的類型。</span><span class="sxs-lookup"><span data-stu-id="d8c24-107">These types are not necessarily the exact store types, but the types the provider uses to support the Entity Framework.</span></span> <span data-ttu-id="d8c24-108">提供者/存放區型別將以實體資料模型 (EDM) 詞彙描述。</span><span class="sxs-lookup"><span data-stu-id="d8c24-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="d8c24-109">資料存放區所支援之函式的參數和傳回型別則以 EDM 詞彙指定。</span><span class="sxs-lookup"><span data-stu-id="d8c24-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8c24-110">需求</span><span class="sxs-lookup"><span data-stu-id="d8c24-110">Requirements</span></span>  
 <span data-ttu-id="d8c24-111">實體框架和資料存儲需要能夠在不丟失或截斷的情況下以已知類型來回傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="d8c24-111">The Entity Framework and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="d8c24-112">提供者資訊清單必須能夠在設計階段中由工具載入，而不需要開啟資料存放區的連接。</span><span class="sxs-lookup"><span data-stu-id="d8c24-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="d8c24-113">實體框架區分大小寫，但基礎資料存儲可能不是。</span><span class="sxs-lookup"><span data-stu-id="d8c24-113">The Entity Framework is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="d8c24-114">在清單中定義和使用 EDM 專案（例如識別碼和類型名稱）時，它們必須使用實體框架區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d8c24-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the Entity Framework case sensitivity.</span></span> <span data-ttu-id="d8c24-115">如果可能區分大小寫的資料存放區項目出現在提供者資訊清單中，就必須在提供者資訊清單中保留該大小寫設定。</span><span class="sxs-lookup"><span data-stu-id="d8c24-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="d8c24-116">實體框架需要所有資料提供程式的提供程式清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-116">The Entity Framework requires a provider manifest for all data providers.</span></span> <span data-ttu-id="d8c24-117">如果嘗試使用實體框架中沒有提供程式清單的提供程式，則將出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8c24-117">If you try to use a provider that does not have a provider manifest with the Entity Framework, you will get an error.</span></span>  
  
 <span data-ttu-id="d8c24-118">下表描述了實體框架在提供程式交互出現異常時將引發的異常類型：</span><span class="sxs-lookup"><span data-stu-id="d8c24-118">The following table describes the kinds of exceptions the Entity Framework would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="d8c24-119">問題</span><span class="sxs-lookup"><span data-stu-id="d8c24-119">Issue</span></span>|<span data-ttu-id="d8c24-120">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d8c24-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="d8c24-121">提供者不支援 DbProviderServices 中的 GetProviderManifest。</span><span class="sxs-lookup"><span data-stu-id="d8c24-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="d8c24-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="d8c24-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="d8c24-123">遺漏提供者資訊清單：嘗試擷取提供者資訊清單時，提供者會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="d8c24-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="d8c24-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="d8c24-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="d8c24-125">無效的提供者資訊清單：嘗試擷取提供者資訊清單時，提供者會傳回無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="d8c24-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="d8c24-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="d8c24-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="d8c24-127">案例</span><span class="sxs-lookup"><span data-stu-id="d8c24-127">Scenarios</span></span>  
 <span data-ttu-id="d8c24-128">提供者應該支援下列案例：</span><span class="sxs-lookup"><span data-stu-id="d8c24-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="d8c24-129">使用對稱型別對應撰寫提供者</span><span class="sxs-lookup"><span data-stu-id="d8c24-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="d8c24-130">您可以為實體框架編寫提供程式，其中每個存儲類型映射到單個 EDM 類型，而不考慮映射方向。</span><span class="sxs-lookup"><span data-stu-id="d8c24-130">You can write a provider for the Entity Framework where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="d8c24-131">若為具有非常簡單對應 (與某個 EDM 型別對應) 的提供者型別，您就可以使用對稱方案，因為型別系統很簡單或符合 EDM 型別。</span><span class="sxs-lookup"><span data-stu-id="d8c24-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="d8c24-132">您可以使用其網域的簡易性並產生靜態宣告式提供者資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="d8c24-133">您可以撰寫具有兩個區段的 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="d8c24-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="d8c24-134">以存放區型別或函式之「EDM 對應項目」詞彙表示的提供者型別清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="d8c24-135">存放區型別具有對應的 EDM 型別。</span><span class="sxs-lookup"><span data-stu-id="d8c24-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="d8c24-136">存放區函式具有對應的 EDM 函式。</span><span class="sxs-lookup"><span data-stu-id="d8c24-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="d8c24-137">例如，varchar 是 SQL Server 型別，但是對應的 EDM 型別是 string。</span><span class="sxs-lookup"><span data-stu-id="d8c24-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="d8c24-138">提供者所支援的函式清單，其中參數和傳回型別是以 EDM 詞彙表示。</span><span class="sxs-lookup"><span data-stu-id="d8c24-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="d8c24-139">使用非對稱型別對應撰寫提供者</span><span class="sxs-lookup"><span data-stu-id="d8c24-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="d8c24-140">為實體框架編寫資料存儲提供程式時，某些類型的 EDM 到提供程式類型映射可能與提供程式到 EDM 類型映射不同。</span><span class="sxs-lookup"><span data-stu-id="d8c24-140">When writing a data store provider for the Entity Framework, the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="d8c24-141">例如，unbounded EDM PrimitiveTypeKind.String 可能會對應至提供者的 nvarchar(4000)，而 nvarchar(4000) 則對應至 EDM PrimitiveTypeKind.String(MaxLength=4000)。</span><span class="sxs-lookup"><span data-stu-id="d8c24-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="d8c24-142">您可以撰寫具有兩個區段的 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="d8c24-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="d8c24-143">以 EDM 詞彙表示的提供者型別清單並且定義兩個方向的對應：EDM 到提供者以及提供者到 EDM。</span><span class="sxs-lookup"><span data-stu-id="d8c24-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="d8c24-144">提供者所支援的函式清單，其中參數和傳回型別是以 EDM 詞彙表示。</span><span class="sxs-lookup"><span data-stu-id="d8c24-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="d8c24-145">提供者資訊清單探索能力</span><span class="sxs-lookup"><span data-stu-id="d8c24-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="d8c24-146">此資訊清單會由實體服務中的許多元件類型 (例如工具或查詢) 間接使用，但是更直接由中繼資料透過資料存放區中繼資料載入器運用。</span><span class="sxs-lookup"><span data-stu-id="d8c24-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="d8c24-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="d8c24-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="d8c24-148">不過，給定的提供者可能會支援不同的存放區或相同存放區的不同版本。</span><span class="sxs-lookup"><span data-stu-id="d8c24-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="d8c24-149">因此，提供者必須針對每個支援的資料存放區報告不同的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="d8c24-150">提供者資訊清單語彙基元</span><span class="sxs-lookup"><span data-stu-id="d8c24-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="d8c24-151">當開啟資料存放區連接時，提供者可以查詢資訊，以便傳回正確的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="d8c24-152">在離線案例中 (無法使用連接資訊或是無法連接至存放區)，可能就無法這樣做。</span><span class="sxs-lookup"><span data-stu-id="d8c24-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="d8c24-153">您可以使用 .ssdl 檔案中 `ProviderManifestToken` 項目的 `Schema` 屬性來識別資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="d8c24-154">這個屬性沒有必要的格式。提供者會選擇識別資訊清單所需的最少資訊，而不必開啟存放區的連接。</span><span class="sxs-lookup"><span data-stu-id="d8c24-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="d8c24-155">例如：</span><span class="sxs-lookup"><span data-stu-id="d8c24-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="d8c24-156">提供者資訊清單程式設計模型</span><span class="sxs-lookup"><span data-stu-id="d8c24-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="d8c24-157">提供者會衍生自 <xref:System.Data.Common.DbXmlEnabledProviderManifest>，以便讓它們以宣告方式指定其資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="d8c24-158">下圖將說明提供者的類別階層：</span><span class="sxs-lookup"><span data-stu-id="d8c24-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="d8c24-159">![無](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="d8c24-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="d8c24-160">探索能力 API</span><span class="sxs-lookup"><span data-stu-id="d8c24-160">Discoverability API</span></span>  
 <span data-ttu-id="d8c24-161">存放區中繼資料載入器 (StoreItemCollection) 會使用資料存放區連接或提供者資訊清單語彙基元來載入提供者資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d8c24-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="d8c24-162">使用資料存放區連接</span><span class="sxs-lookup"><span data-stu-id="d8c24-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="d8c24-163">當資料存儲連接可用時，調用<xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType>以返回傳遞給 方法的<xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A>權杖，該方法將返回<xref:System.Data.Common.DbProviderManifest>。</span><span class="sxs-lookup"><span data-stu-id="d8c24-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="d8c24-164">此方法委託給提供程式的`GetDbProviderManifestToken`實現。</span><span class="sxs-lookup"><span data-stu-id="d8c24-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="d8c24-165">使用提供者資訊清單語彙基元</span><span class="sxs-lookup"><span data-stu-id="d8c24-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="d8c24-166">在離線案例中，系統會從 SSDL 表示中挑選語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d8c24-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="d8c24-167">SSDL 允許您指定提供程式清單權杖（有關詳細資訊，請參閱[架構元素 （SSDL）。](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl)</span><span class="sxs-lookup"><span data-stu-id="d8c24-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="d8c24-168">例如，如果無法開啟連接，SSDL 就會具有指定資訊清單之相關資訊的提供者資訊清單語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d8c24-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="d8c24-169">提供者資訊清單結構描述</span><span class="sxs-lookup"><span data-stu-id="d8c24-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="d8c24-170">針對每個提供者所定義的資訊結構描述都包含要由中繼資料取用的靜態資訊：</span><span class="sxs-lookup"><span data-stu-id="d8c24-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a><span data-ttu-id="d8c24-171">Types 節點</span><span class="sxs-lookup"><span data-stu-id="d8c24-171">Types Node</span></span>  
 <span data-ttu-id="d8c24-172">提供者資訊清單中的 Types 節點會包含資料存放區原本支援或透過提供者支援之型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d8c24-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="d8c24-173">Type 節點</span><span class="sxs-lookup"><span data-stu-id="d8c24-173">Type Node</span></span>  
 <span data-ttu-id="d8c24-174">每個 Type 節點都會以 EDM 的詞彙定義提供者類型。</span><span class="sxs-lookup"><span data-stu-id="d8c24-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="d8c24-175">Type 節點會描述提供者類型的名稱、它所對應之模型型別的相關資訊，以及描述該型別對應的 Facet。</span><span class="sxs-lookup"><span data-stu-id="d8c24-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="d8c24-176">若要在提供者資訊清單中表示這種型別資訊，每個 TypeInformation 宣告都必須針對每個型別定義許多 Facet 描述：</span><span class="sxs-lookup"><span data-stu-id="d8c24-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="d8c24-177">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="d8c24-177">Attribute Name</span></span>|<span data-ttu-id="d8c24-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="d8c24-178">Data Type</span></span>|<span data-ttu-id="d8c24-179">必要</span><span class="sxs-lookup"><span data-stu-id="d8c24-179">Required</span></span>|<span data-ttu-id="d8c24-180">預設值</span><span class="sxs-lookup"><span data-stu-id="d8c24-180">Default Value</span></span>|<span data-ttu-id="d8c24-181">描述</span><span class="sxs-lookup"><span data-stu-id="d8c24-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="d8c24-182">名稱</span><span class="sxs-lookup"><span data-stu-id="d8c24-182">Name</span></span>|<span data-ttu-id="d8c24-183">String</span><span class="sxs-lookup"><span data-stu-id="d8c24-183">String</span></span>|<span data-ttu-id="d8c24-184">是</span><span class="sxs-lookup"><span data-stu-id="d8c24-184">Yes</span></span>|<span data-ttu-id="d8c24-185">n/a</span><span class="sxs-lookup"><span data-stu-id="d8c24-185">n/a</span></span>|<span data-ttu-id="d8c24-186">提供者特有的資料型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c24-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="d8c24-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="d8c24-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="d8c24-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="d8c24-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="d8c24-189">是</span><span class="sxs-lookup"><span data-stu-id="d8c24-189">Yes</span></span>|<span data-ttu-id="d8c24-190">n/a</span><span class="sxs-lookup"><span data-stu-id="d8c24-190">n/a</span></span>|<span data-ttu-id="d8c24-191">EDM 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c24-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="d8c24-192">Function 節點</span><span class="sxs-lookup"><span data-stu-id="d8c24-192">Function Node</span></span>  
 <span data-ttu-id="d8c24-193">每個 Function 都會定義透過提供者所提供的單一函式。</span><span class="sxs-lookup"><span data-stu-id="d8c24-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="d8c24-194">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="d8c24-194">Attribute Name</span></span>|<span data-ttu-id="d8c24-195">資料類型</span><span class="sxs-lookup"><span data-stu-id="d8c24-195">Data Type</span></span>|<span data-ttu-id="d8c24-196">必要</span><span class="sxs-lookup"><span data-stu-id="d8c24-196">Required</span></span>|<span data-ttu-id="d8c24-197">預設值</span><span class="sxs-lookup"><span data-stu-id="d8c24-197">Default Value</span></span>|<span data-ttu-id="d8c24-198">描述</span><span class="sxs-lookup"><span data-stu-id="d8c24-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="d8c24-199">名稱</span><span class="sxs-lookup"><span data-stu-id="d8c24-199">Name</span></span>|<span data-ttu-id="d8c24-200">String</span><span class="sxs-lookup"><span data-stu-id="d8c24-200">String</span></span>|<span data-ttu-id="d8c24-201">是</span><span class="sxs-lookup"><span data-stu-id="d8c24-201">Yes</span></span>|<span data-ttu-id="d8c24-202">n/a</span><span class="sxs-lookup"><span data-stu-id="d8c24-202">n/a</span></span>|<span data-ttu-id="d8c24-203">函式的識別碼/名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c24-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="d8c24-204">ReturnType</span><span class="sxs-lookup"><span data-stu-id="d8c24-204">ReturnType</span></span>|<span data-ttu-id="d8c24-205">String</span><span class="sxs-lookup"><span data-stu-id="d8c24-205">String</span></span>|<span data-ttu-id="d8c24-206">否</span><span class="sxs-lookup"><span data-stu-id="d8c24-206">No</span></span>|<span data-ttu-id="d8c24-207">Void</span><span class="sxs-lookup"><span data-stu-id="d8c24-207">Void</span></span>|<span data-ttu-id="d8c24-208">函式的 EDM 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d8c24-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="d8c24-209">Aggregate</span><span class="sxs-lookup"><span data-stu-id="d8c24-209">Aggregate</span></span>|<span data-ttu-id="d8c24-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8c24-210">Boolean</span></span>|<span data-ttu-id="d8c24-211">否</span><span class="sxs-lookup"><span data-stu-id="d8c24-211">No</span></span>|<span data-ttu-id="d8c24-212">False</span><span class="sxs-lookup"><span data-stu-id="d8c24-212">False</span></span>|<span data-ttu-id="d8c24-213">如果此函式是彙總函式，則為 True。</span><span class="sxs-lookup"><span data-stu-id="d8c24-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="d8c24-214">BuiltIn</span><span class="sxs-lookup"><span data-stu-id="d8c24-214">BuiltIn</span></span>|<span data-ttu-id="d8c24-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8c24-215">Boolean</span></span>|<span data-ttu-id="d8c24-216">否</span><span class="sxs-lookup"><span data-stu-id="d8c24-216">No</span></span>|<span data-ttu-id="d8c24-217">True</span><span class="sxs-lookup"><span data-stu-id="d8c24-217">True</span></span>|<span data-ttu-id="d8c24-218">如果此函式內建在資料存放區中，則為 True。</span><span class="sxs-lookup"><span data-stu-id="d8c24-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="d8c24-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="d8c24-219">StoreFunctionName</span></span>|<span data-ttu-id="d8c24-220">String</span><span class="sxs-lookup"><span data-stu-id="d8c24-220">String</span></span>|<span data-ttu-id="d8c24-221">否</span><span class="sxs-lookup"><span data-stu-id="d8c24-221">No</span></span>|<span data-ttu-id="d8c24-222">\<Name></span><span class="sxs-lookup"><span data-stu-id="d8c24-222">\<Name></span></span>|<span data-ttu-id="d8c24-223">資料存放區中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c24-223">Function Name in the data store.</span></span>  <span data-ttu-id="d8c24-224">允許重新導向函式名稱的層級。</span><span class="sxs-lookup"><span data-stu-id="d8c24-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="d8c24-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="d8c24-225">NiladicFunction</span></span>|<span data-ttu-id="d8c24-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="d8c24-226">Boolean</span></span>|<span data-ttu-id="d8c24-227">否</span><span class="sxs-lookup"><span data-stu-id="d8c24-227">No</span></span>|<span data-ttu-id="d8c24-228">False</span><span class="sxs-lookup"><span data-stu-id="d8c24-228">False</span></span>|<span data-ttu-id="d8c24-229">如果此函式不需要參數，而且會在不使用任何參數的情況下呼叫，則為 True。</span><span class="sxs-lookup"><span data-stu-id="d8c24-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="d8c24-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="d8c24-230">ParameterType</span></span><br /><br /> <span data-ttu-id="d8c24-231">語意</span><span class="sxs-lookup"><span data-stu-id="d8c24-231">Semantics</span></span>|<span data-ttu-id="d8c24-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="d8c24-232">ParameterSemantics</span></span>|<span data-ttu-id="d8c24-233">否</span><span class="sxs-lookup"><span data-stu-id="d8c24-233">No</span></span>|<span data-ttu-id="d8c24-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="d8c24-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="d8c24-235">轉換</span><span class="sxs-lookup"><span data-stu-id="d8c24-235">Conversion</span></span>|<span data-ttu-id="d8c24-236">選擇查詢管線應該如何處理參數型別替代項目：</span><span class="sxs-lookup"><span data-stu-id="d8c24-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="d8c24-237">- 僅精確匹配</span><span class="sxs-lookup"><span data-stu-id="d8c24-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="d8c24-238">- 允許隱式促銷</span><span class="sxs-lookup"><span data-stu-id="d8c24-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="d8c24-239">- 允許隱式轉換</span><span class="sxs-lookup"><span data-stu-id="d8c24-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="d8c24-240">**Parameters 節點**</span><span class="sxs-lookup"><span data-stu-id="d8c24-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="d8c24-241">每個函式都具有一個或多個 Parameter 節點的集合。</span><span class="sxs-lookup"><span data-stu-id="d8c24-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="d8c24-242">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="d8c24-242">Attribute Name</span></span>|<span data-ttu-id="d8c24-243">資料類型</span><span class="sxs-lookup"><span data-stu-id="d8c24-243">Data Type</span></span>|<span data-ttu-id="d8c24-244">必要</span><span class="sxs-lookup"><span data-stu-id="d8c24-244">Required</span></span>|<span data-ttu-id="d8c24-245">預設值</span><span class="sxs-lookup"><span data-stu-id="d8c24-245">Default Value</span></span>|<span data-ttu-id="d8c24-246">描述</span><span class="sxs-lookup"><span data-stu-id="d8c24-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="d8c24-247">名稱</span><span class="sxs-lookup"><span data-stu-id="d8c24-247">Name</span></span>|<span data-ttu-id="d8c24-248">String</span><span class="sxs-lookup"><span data-stu-id="d8c24-248">String</span></span>|<span data-ttu-id="d8c24-249">是</span><span class="sxs-lookup"><span data-stu-id="d8c24-249">Yes</span></span>|<span data-ttu-id="d8c24-250">n/a</span><span class="sxs-lookup"><span data-stu-id="d8c24-250">n/a</span></span>|<span data-ttu-id="d8c24-251">參數的識別碼/名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c24-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="d8c24-252">類型</span><span class="sxs-lookup"><span data-stu-id="d8c24-252">Type</span></span>|<span data-ttu-id="d8c24-253">String</span><span class="sxs-lookup"><span data-stu-id="d8c24-253">String</span></span>|<span data-ttu-id="d8c24-254">是</span><span class="sxs-lookup"><span data-stu-id="d8c24-254">Yes</span></span>|<span data-ttu-id="d8c24-255">n/a</span><span class="sxs-lookup"><span data-stu-id="d8c24-255">n/a</span></span>|<span data-ttu-id="d8c24-256">參數的 EDM 型別。</span><span class="sxs-lookup"><span data-stu-id="d8c24-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="d8c24-257">[模式]</span><span class="sxs-lookup"><span data-stu-id="d8c24-257">Mode</span></span>|<span data-ttu-id="d8c24-258">參數</span><span class="sxs-lookup"><span data-stu-id="d8c24-258">Parameter</span></span><br /><br /> <span data-ttu-id="d8c24-259">方向</span><span class="sxs-lookup"><span data-stu-id="d8c24-259">Direction</span></span>|<span data-ttu-id="d8c24-260">是</span><span class="sxs-lookup"><span data-stu-id="d8c24-260">Yes</span></span>|<span data-ttu-id="d8c24-261">n/a</span><span class="sxs-lookup"><span data-stu-id="d8c24-261">n/a</span></span>|<span data-ttu-id="d8c24-262">參數的方向：</span><span class="sxs-lookup"><span data-stu-id="d8c24-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="d8c24-263">- 在</span><span class="sxs-lookup"><span data-stu-id="d8c24-263">-   in</span></span><br /><span data-ttu-id="d8c24-264">- 出</span><span class="sxs-lookup"><span data-stu-id="d8c24-264">-   out</span></span><br /><span data-ttu-id="d8c24-265">- 出</span><span class="sxs-lookup"><span data-stu-id="d8c24-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="d8c24-266">Namespace 屬性</span><span class="sxs-lookup"><span data-stu-id="d8c24-266">Namespace Attribute</span></span>  
 <span data-ttu-id="d8c24-267">每個資料存放區提供者都必須針對資訊清單中定義的資訊定義一個命名空間或命名空間群組。</span><span class="sxs-lookup"><span data-stu-id="d8c24-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="d8c24-268">這個命名空間可用於 Entity SQL 查詢中，以便解析函式和型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c24-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="d8c24-269">例如：SqlServer。</span><span class="sxs-lookup"><span data-stu-id="d8c24-269">For instance: SqlServer.</span></span> <span data-ttu-id="d8c24-270">不過，該命名空間必須與標準命名空間 EDM 不同，後者是實體服務針對要由 Entity SQL 查詢所支援之標準函式定義的。</span><span class="sxs-lookup"><span data-stu-id="d8c24-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c24-271">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8c24-271">See also</span></span>

- [<span data-ttu-id="d8c24-272">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="d8c24-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
