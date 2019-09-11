---
title: 提供者資訊清單規格
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: cc58bbc82f3930f087b5da0c64afb4f9f03e905b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854498"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="52516-102">提供者資訊清單規格</span><span class="sxs-lookup"><span data-stu-id="52516-102">Provider Manifest Specification</span></span>
<span data-ttu-id="52516-103">本節將討論資料存放區提供者如何支援資料存放區中的型別與函式。</span><span class="sxs-lookup"><span data-stu-id="52516-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="52516-104">雖然實體服務的運作與特定資料存放區提供者無關，不過它仍然允許資料提供者明確定義模型、對應和查詢與基礎資料存放區互動的方式。</span><span class="sxs-lookup"><span data-stu-id="52516-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="52516-105">如果沒有抽象層，實體服務的目標只能設定為特定資料存放區或資料提供者。</span><span class="sxs-lookup"><span data-stu-id="52516-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="52516-106">基礎資料庫會直接或間接支援提供者所支援的型別。</span><span class="sxs-lookup"><span data-stu-id="52516-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="52516-107">這些類型不一定是確切的存放區類型，而是提供者用來支援 Entity Framework 的類型。</span><span class="sxs-lookup"><span data-stu-id="52516-107">These types are not necessarily the exact store types, but the types the provider uses to support the Entity Framework.</span></span> <span data-ttu-id="52516-108">提供者/存放區型別將以實體資料模型 (EDM) 詞彙描述。</span><span class="sxs-lookup"><span data-stu-id="52516-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="52516-109">資料存放區所支援之函式的參數和傳回型別則以 EDM 詞彙指定。</span><span class="sxs-lookup"><span data-stu-id="52516-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52516-110">需求</span><span class="sxs-lookup"><span data-stu-id="52516-110">Requirements</span></span>  
 <span data-ttu-id="52516-111">Entity Framework 和資料存放區必須能夠在已知型別中來回傳遞資料，而不會遺失或截斷資料。</span><span class="sxs-lookup"><span data-stu-id="52516-111">The Entity Framework and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="52516-112">提供者資訊清單必須能夠在設計階段中由工具載入，而不需要開啟資料存放區的連接。</span><span class="sxs-lookup"><span data-stu-id="52516-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="52516-113">Entity Framework 區分大小寫，但基礎資料存放區可能不是。</span><span class="sxs-lookup"><span data-stu-id="52516-113">The Entity Framework is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="52516-114">在資訊清單中定義和使用 EDM 成品（例如，識別碼和型別名稱）時，必須使用 Entity Framework 區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="52516-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the Entity Framework case sensitivity.</span></span> <span data-ttu-id="52516-115">如果可能區分大小寫的資料存放區項目出現在提供者資訊清單中，就必須在提供者資訊清單中保留該大小寫設定。</span><span class="sxs-lookup"><span data-stu-id="52516-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="52516-116">Entity Framework 需要所有資料提供者的提供者資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-116">The Entity Framework requires a provider manifest for all data providers.</span></span> <span data-ttu-id="52516-117">如果您嘗試使用沒有提供者資訊清單的提供者搭配 Entity Framework，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="52516-117">If you try to use a provider that does not have a provider manifest with the Entity Framework, you will get an error.</span></span>  
  
 <span data-ttu-id="52516-118">下表描述當透過提供者互動引發例外狀況時，Entity Framework 會擲回的例外狀況類型：</span><span class="sxs-lookup"><span data-stu-id="52516-118">The following table describes the kinds of exceptions the Entity Framework would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="52516-119">問題</span><span class="sxs-lookup"><span data-stu-id="52516-119">Issue</span></span>|<span data-ttu-id="52516-120">例外</span><span class="sxs-lookup"><span data-stu-id="52516-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="52516-121">提供者不支援 DbProviderServices 中的 GetProviderManifest。</span><span class="sxs-lookup"><span data-stu-id="52516-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="52516-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="52516-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="52516-123">遺漏提供者資訊清單：嘗試擷取提供者資訊清單時，提供者會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="52516-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="52516-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="52516-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="52516-125">無效的提供者資訊清單：嘗試擷取提供者資訊清單時，提供者會傳回無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="52516-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="52516-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="52516-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="52516-127">案例</span><span class="sxs-lookup"><span data-stu-id="52516-127">Scenarios</span></span>  
 <span data-ttu-id="52516-128">提供者應該支援下列案例：</span><span class="sxs-lookup"><span data-stu-id="52516-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="52516-129">使用對稱型別對應撰寫提供者</span><span class="sxs-lookup"><span data-stu-id="52516-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="52516-130">您可以撰寫 Entity Framework 的提供者，其中每個存放區類型都會對應至單一 EDM 類型，不論對應方向為何。</span><span class="sxs-lookup"><span data-stu-id="52516-130">You can write a provider for the Entity Framework where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="52516-131">若為具有非常簡單對應 (與某個 EDM 型別對應) 的提供者型別，您就可以使用對稱方案，因為型別系統很簡單或符合 EDM 型別。</span><span class="sxs-lookup"><span data-stu-id="52516-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="52516-132">您可以使用其網域的簡易性並產生靜態宣告式提供者資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="52516-133">您可以撰寫具有兩個區段的 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="52516-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="52516-134">以存放區型別或函式之「EDM 對應項目」詞彙表示的提供者型別清單。</span><span class="sxs-lookup"><span data-stu-id="52516-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="52516-135">存放區型別具有對應的 EDM 型別。</span><span class="sxs-lookup"><span data-stu-id="52516-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="52516-136">存放區函式具有對應的 EDM 函式。</span><span class="sxs-lookup"><span data-stu-id="52516-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="52516-137">例如，varchar 是 SQL Server 型別，但是對應的 EDM 型別是 string。</span><span class="sxs-lookup"><span data-stu-id="52516-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="52516-138">提供者所支援的函式清單，其中參數和傳回型別是以 EDM 詞彙表示。</span><span class="sxs-lookup"><span data-stu-id="52516-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="52516-139">使用非對稱型別對應撰寫提供者</span><span class="sxs-lookup"><span data-stu-id="52516-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="52516-140">撰寫 Entity Framework 的資料存放區提供者時，某些類型的 EDM 對提供者類型對應可能會與提供者對 EDM 類型的對應不同。</span><span class="sxs-lookup"><span data-stu-id="52516-140">When writing a data store provider for the Entity Framework, the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="52516-141">例如，unbounded EDM PrimitiveTypeKind.String 可能會對應至提供者的 nvarchar(4000)，而 nvarchar(4000) 則對應至 EDM PrimitiveTypeKind.String(MaxLength=4000)。</span><span class="sxs-lookup"><span data-stu-id="52516-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="52516-142">您可以撰寫具有兩個區段的 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="52516-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="52516-143">以 EDM 詞彙表示的提供者類型清單，並定義兩個方向的對應：EDM 到提供者和提供者到 EDM。</span><span class="sxs-lookup"><span data-stu-id="52516-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="52516-144">提供者所支援的函式清單，其中參數和傳回型別是以 EDM 詞彙表示。</span><span class="sxs-lookup"><span data-stu-id="52516-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="52516-145">提供者資訊清單探索能力</span><span class="sxs-lookup"><span data-stu-id="52516-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="52516-146">此資訊清單會由實體服務中的許多元件類型 (例如工具或查詢) 間接使用，但是更直接由中繼資料透過資料存放區中繼資料載入器運用。</span><span class="sxs-lookup"><span data-stu-id="52516-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="52516-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="52516-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="52516-148">不過，給定的提供者可能會支援不同的存放區或相同存放區的不同版本。</span><span class="sxs-lookup"><span data-stu-id="52516-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="52516-149">因此，提供者必須針對每個支援的資料存放區報告不同的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="52516-150">提供者資訊清單語彙基元</span><span class="sxs-lookup"><span data-stu-id="52516-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="52516-151">當開啟資料存放區連接時，提供者可以查詢資訊，以便傳回正確的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="52516-152">在離線案例中 (無法使用連接資訊或是無法連接至存放區)，可能就無法這樣做。</span><span class="sxs-lookup"><span data-stu-id="52516-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="52516-153">您可以使用 .ssdl 檔案中 `ProviderManifestToken` 項目的 `Schema` 屬性來識別資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="52516-154">這個屬性沒有必要的格式。提供者會選擇識別資訊清單所需的最少資訊，而不必開啟存放區的連接。</span><span class="sxs-lookup"><span data-stu-id="52516-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="52516-155">例如：</span><span class="sxs-lookup"><span data-stu-id="52516-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="52516-156">提供者資訊清單程式設計模型</span><span class="sxs-lookup"><span data-stu-id="52516-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="52516-157">提供者會衍生自 <xref:System.Data.Common.DbXmlEnabledProviderManifest>，以便讓它們以宣告方式指定其資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="52516-158">下圖將說明提供者的類別階層：</span><span class="sxs-lookup"><span data-stu-id="52516-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="52516-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="52516-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="52516-160">探索能力 API</span><span class="sxs-lookup"><span data-stu-id="52516-160">Discoverability API</span></span>  
 <span data-ttu-id="52516-161">存放區中繼資料載入器 (StoreItemCollection) 會使用資料存放區連接或提供者資訊清單語彙基元來載入提供者資訊清單。</span><span class="sxs-lookup"><span data-stu-id="52516-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="52516-162">使用資料存放區連接</span><span class="sxs-lookup"><span data-stu-id="52516-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="52516-163">當有可用的資料存放區連接時<xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> ，呼叫以傳回傳遞<xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A>至方法的 token，這<xref:System.Data.Common.DbProviderManifest>會傳回。</span><span class="sxs-lookup"><span data-stu-id="52516-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="52516-164">這個方法會委派給提供者的執行`GetDbProviderManifestToken`。</span><span class="sxs-lookup"><span data-stu-id="52516-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="52516-165">使用提供者資訊清單語彙基元</span><span class="sxs-lookup"><span data-stu-id="52516-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="52516-166">在離線案例中，系統會從 SSDL 表示中挑選語彙基元。</span><span class="sxs-lookup"><span data-stu-id="52516-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="52516-167">SSDL 可讓您指定 ProviderManifestToken （如需詳細資訊，請參閱[Schema 元素（SSDL）](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) ）。</span><span class="sxs-lookup"><span data-stu-id="52516-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="52516-168">例如，如果無法開啟連接，SSDL 就會具有指定資訊清單之相關資訊的提供者資訊清單語彙基元。</span><span class="sxs-lookup"><span data-stu-id="52516-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="52516-169">提供者資訊清單結構描述</span><span class="sxs-lookup"><span data-stu-id="52516-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="52516-170">針對每個提供者所定義的資訊結構描述都包含要由中繼資料取用的靜態資訊：</span><span class="sxs-lookup"><span data-stu-id="52516-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="52516-171">Types 節點</span><span class="sxs-lookup"><span data-stu-id="52516-171">Types Node</span></span>  
 <span data-ttu-id="52516-172">提供者資訊清單中的 Types 節點會包含資料存放區原本支援或透過提供者支援之型別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="52516-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="52516-173">Type 節點</span><span class="sxs-lookup"><span data-stu-id="52516-173">Type Node</span></span>  
 <span data-ttu-id="52516-174">每個 Type 節點都會以 EDM 的詞彙定義提供者類型。</span><span class="sxs-lookup"><span data-stu-id="52516-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="52516-175">Type 節點會描述提供者類型的名稱、它所對應之模型型別的相關資訊，以及描述該型別對應的 Facet。</span><span class="sxs-lookup"><span data-stu-id="52516-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="52516-176">若要在提供者資訊清單中表示這種型別資訊，每個 TypeInformation 宣告都必須針對每個型別定義許多 Facet 描述：</span><span class="sxs-lookup"><span data-stu-id="52516-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="52516-177">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="52516-177">Attribute Name</span></span>|<span data-ttu-id="52516-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="52516-178">Data Type</span></span>|<span data-ttu-id="52516-179">必要</span><span class="sxs-lookup"><span data-stu-id="52516-179">Required</span></span>|<span data-ttu-id="52516-180">預設值</span><span class="sxs-lookup"><span data-stu-id="52516-180">Default Value</span></span>|<span data-ttu-id="52516-181">描述</span><span class="sxs-lookup"><span data-stu-id="52516-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="52516-182">名稱</span><span class="sxs-lookup"><span data-stu-id="52516-182">Name</span></span>|<span data-ttu-id="52516-183">String</span><span class="sxs-lookup"><span data-stu-id="52516-183">String</span></span>|<span data-ttu-id="52516-184">是</span><span class="sxs-lookup"><span data-stu-id="52516-184">Yes</span></span>|<span data-ttu-id="52516-185">N/A</span><span class="sxs-lookup"><span data-stu-id="52516-185">n/a</span></span>|<span data-ttu-id="52516-186">提供者特有的資料型別名稱。</span><span class="sxs-lookup"><span data-stu-id="52516-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="52516-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="52516-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="52516-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="52516-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="52516-189">是</span><span class="sxs-lookup"><span data-stu-id="52516-189">Yes</span></span>|<span data-ttu-id="52516-190">N/A</span><span class="sxs-lookup"><span data-stu-id="52516-190">n/a</span></span>|<span data-ttu-id="52516-191">EDM 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="52516-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="52516-192">Function 節點</span><span class="sxs-lookup"><span data-stu-id="52516-192">Function Node</span></span>  
 <span data-ttu-id="52516-193">每個 Function 都會定義透過提供者所提供的單一函式。</span><span class="sxs-lookup"><span data-stu-id="52516-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="52516-194">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="52516-194">Attribute Name</span></span>|<span data-ttu-id="52516-195">資料類型</span><span class="sxs-lookup"><span data-stu-id="52516-195">Data Type</span></span>|<span data-ttu-id="52516-196">必要</span><span class="sxs-lookup"><span data-stu-id="52516-196">Required</span></span>|<span data-ttu-id="52516-197">預設值</span><span class="sxs-lookup"><span data-stu-id="52516-197">Default Value</span></span>|<span data-ttu-id="52516-198">描述</span><span class="sxs-lookup"><span data-stu-id="52516-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="52516-199">名稱</span><span class="sxs-lookup"><span data-stu-id="52516-199">Name</span></span>|<span data-ttu-id="52516-200">String</span><span class="sxs-lookup"><span data-stu-id="52516-200">String</span></span>|<span data-ttu-id="52516-201">是</span><span class="sxs-lookup"><span data-stu-id="52516-201">Yes</span></span>|<span data-ttu-id="52516-202">N/A</span><span class="sxs-lookup"><span data-stu-id="52516-202">n/a</span></span>|<span data-ttu-id="52516-203">函式的識別碼/名稱。</span><span class="sxs-lookup"><span data-stu-id="52516-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="52516-204">ReturnType</span><span class="sxs-lookup"><span data-stu-id="52516-204">ReturnType</span></span>|<span data-ttu-id="52516-205">String</span><span class="sxs-lookup"><span data-stu-id="52516-205">String</span></span>|<span data-ttu-id="52516-206">否</span><span class="sxs-lookup"><span data-stu-id="52516-206">No</span></span>|<span data-ttu-id="52516-207">Void</span><span class="sxs-lookup"><span data-stu-id="52516-207">Void</span></span>|<span data-ttu-id="52516-208">函式的 EDM 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="52516-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="52516-209">Aggregate</span><span class="sxs-lookup"><span data-stu-id="52516-209">Aggregate</span></span>|<span data-ttu-id="52516-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="52516-210">Boolean</span></span>|<span data-ttu-id="52516-211">否</span><span class="sxs-lookup"><span data-stu-id="52516-211">No</span></span>|<span data-ttu-id="52516-212">偽</span><span class="sxs-lookup"><span data-stu-id="52516-212">False</span></span>|<span data-ttu-id="52516-213">如果此函式是彙總函式，則為 True。</span><span class="sxs-lookup"><span data-stu-id="52516-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="52516-214">BuiltIn</span><span class="sxs-lookup"><span data-stu-id="52516-214">BuiltIn</span></span>|<span data-ttu-id="52516-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="52516-215">Boolean</span></span>|<span data-ttu-id="52516-216">否</span><span class="sxs-lookup"><span data-stu-id="52516-216">No</span></span>|<span data-ttu-id="52516-217">True</span><span class="sxs-lookup"><span data-stu-id="52516-217">True</span></span>|<span data-ttu-id="52516-218">如果此函式內建在資料存放區中，則為 True。</span><span class="sxs-lookup"><span data-stu-id="52516-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="52516-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="52516-219">StoreFunctionName</span></span>|<span data-ttu-id="52516-220">String</span><span class="sxs-lookup"><span data-stu-id="52516-220">String</span></span>|<span data-ttu-id="52516-221">否</span><span class="sxs-lookup"><span data-stu-id="52516-221">No</span></span>|<span data-ttu-id="52516-222">\<名稱 ></span><span class="sxs-lookup"><span data-stu-id="52516-222">\<Name></span></span>|<span data-ttu-id="52516-223">資料存放區中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="52516-223">Function Name in the data store.</span></span>  <span data-ttu-id="52516-224">允許重新導向函式名稱的層級。</span><span class="sxs-lookup"><span data-stu-id="52516-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="52516-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="52516-225">NiladicFunction</span></span>|<span data-ttu-id="52516-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="52516-226">Boolean</span></span>|<span data-ttu-id="52516-227">否</span><span class="sxs-lookup"><span data-stu-id="52516-227">No</span></span>|<span data-ttu-id="52516-228">偽</span><span class="sxs-lookup"><span data-stu-id="52516-228">False</span></span>|<span data-ttu-id="52516-229">如果此函式不需要參數，而且會在不使用任何參數的情況下呼叫，則為 True。</span><span class="sxs-lookup"><span data-stu-id="52516-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="52516-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="52516-230">ParameterType</span></span><br /><br /> <span data-ttu-id="52516-231">語意</span><span class="sxs-lookup"><span data-stu-id="52516-231">Semantics</span></span>|<span data-ttu-id="52516-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="52516-232">ParameterSemantics</span></span>|<span data-ttu-id="52516-233">否</span><span class="sxs-lookup"><span data-stu-id="52516-233">No</span></span>|<span data-ttu-id="52516-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="52516-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="52516-235">轉換</span><span class="sxs-lookup"><span data-stu-id="52516-235">Conversion</span></span>|<span data-ttu-id="52516-236">選擇查詢管線應該如何處理參數型別替代項目：</span><span class="sxs-lookup"><span data-stu-id="52516-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="52516-237">-   ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="52516-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="52516-238">-AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="52516-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="52516-239">-AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="52516-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="52516-240">**參數節點**</span><span class="sxs-lookup"><span data-stu-id="52516-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="52516-241">每個函式都具有一個或多個 Parameter 節點的集合。</span><span class="sxs-lookup"><span data-stu-id="52516-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="52516-242">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="52516-242">Attribute Name</span></span>|<span data-ttu-id="52516-243">資料類型</span><span class="sxs-lookup"><span data-stu-id="52516-243">Data Type</span></span>|<span data-ttu-id="52516-244">必要</span><span class="sxs-lookup"><span data-stu-id="52516-244">Required</span></span>|<span data-ttu-id="52516-245">預設值</span><span class="sxs-lookup"><span data-stu-id="52516-245">Default Value</span></span>|<span data-ttu-id="52516-246">描述</span><span class="sxs-lookup"><span data-stu-id="52516-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="52516-247">名稱</span><span class="sxs-lookup"><span data-stu-id="52516-247">Name</span></span>|<span data-ttu-id="52516-248">String</span><span class="sxs-lookup"><span data-stu-id="52516-248">String</span></span>|<span data-ttu-id="52516-249">是</span><span class="sxs-lookup"><span data-stu-id="52516-249">Yes</span></span>|<span data-ttu-id="52516-250">N/A</span><span class="sxs-lookup"><span data-stu-id="52516-250">n/a</span></span>|<span data-ttu-id="52516-251">參數的識別碼/名稱。</span><span class="sxs-lookup"><span data-stu-id="52516-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="52516-252">類型</span><span class="sxs-lookup"><span data-stu-id="52516-252">Type</span></span>|<span data-ttu-id="52516-253">String</span><span class="sxs-lookup"><span data-stu-id="52516-253">String</span></span>|<span data-ttu-id="52516-254">是</span><span class="sxs-lookup"><span data-stu-id="52516-254">Yes</span></span>|<span data-ttu-id="52516-255">N/A</span><span class="sxs-lookup"><span data-stu-id="52516-255">n/a</span></span>|<span data-ttu-id="52516-256">參數的 EDM 型別。</span><span class="sxs-lookup"><span data-stu-id="52516-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="52516-257">模式</span><span class="sxs-lookup"><span data-stu-id="52516-257">Mode</span></span>|<span data-ttu-id="52516-258">參數</span><span class="sxs-lookup"><span data-stu-id="52516-258">Parameter</span></span><br /><br /> <span data-ttu-id="52516-259">方向</span><span class="sxs-lookup"><span data-stu-id="52516-259">Direction</span></span>|<span data-ttu-id="52516-260">是</span><span class="sxs-lookup"><span data-stu-id="52516-260">Yes</span></span>|<span data-ttu-id="52516-261">N/A</span><span class="sxs-lookup"><span data-stu-id="52516-261">n/a</span></span>|<span data-ttu-id="52516-262">參數的方向：</span><span class="sxs-lookup"><span data-stu-id="52516-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="52516-263">-in</span><span class="sxs-lookup"><span data-stu-id="52516-263">-   in</span></span><br /><span data-ttu-id="52516-264">-out</span><span class="sxs-lookup"><span data-stu-id="52516-264">-   out</span></span><br /><span data-ttu-id="52516-265">-inout</span><span class="sxs-lookup"><span data-stu-id="52516-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="52516-266">Namespace 屬性</span><span class="sxs-lookup"><span data-stu-id="52516-266">Namespace Attribute</span></span>  
 <span data-ttu-id="52516-267">每個資料存放區提供者都必須針對資訊清單中定義的資訊定義一個命名空間或命名空間群組。</span><span class="sxs-lookup"><span data-stu-id="52516-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="52516-268">這個命名空間可用於 Entity SQL 查詢中，以便解析函式和型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="52516-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="52516-269">若是執行個體：SqlServer.</span><span class="sxs-lookup"><span data-stu-id="52516-269">For instance: SqlServer.</span></span> <span data-ttu-id="52516-270">不過，該命名空間必須與標準命名空間 EDM 不同，後者是實體服務針對要由 Entity SQL 查詢所支援之標準函式定義的。</span><span class="sxs-lookup"><span data-stu-id="52516-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52516-271">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52516-271">See also</span></span>

- [<span data-ttu-id="52516-272">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="52516-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
