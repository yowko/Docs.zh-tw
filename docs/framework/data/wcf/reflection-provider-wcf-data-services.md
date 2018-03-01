---
title: "反映提供者 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 617754fcd9515f080dc6cf8ae923c2c6fc34ad3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="reflection-provider-wcf-data-services"></a><span data-ttu-id="31876-102">反映提供者 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="31876-102">Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="31876-103">除了透過 Entity Framework 從資料模型公開資料外，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 還可以公開在實體架構模型中未嚴格定義的資料。</span><span class="sxs-lookup"><span data-stu-id="31876-103">In addition to exposing data from a data model through the Entity Framework, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] can expose data that is not strictly defined in an entity-based model.</span></span> <span data-ttu-id="31876-104">反映提供者會公開類別中的資料，而這些類別會傳回實作 <xref:System.Linq.IQueryable%601> 介面的類型。</span><span class="sxs-lookup"><span data-stu-id="31876-104">The reflection provider exposes data in classes that return types that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="31876-105"> 使用反映來推斷這些類別的資料模型，而且可以針對資源將定址架構的查詢轉譯為 Language Integrated Query (LINQ) 架構的查詢 (針對已公開的 <xref:System.Linq.IQueryable%601> 類型)。</span><span class="sxs-lookup"><span data-stu-id="31876-105"> uses reflection to infer a data model for these classes and can translate address-based queries against resources into language integrated query (LINQ)-based queries against the exposed <xref:System.Linq.IQueryable%601> types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31876-106">您可以使用 <xref:System.Linq.Queryable.AsQueryable%2A> 方法，從實作 <xref:System.Linq.IQueryable%601> 介面的任何類別傳回 <xref:System.Collections.Generic.IEnumerable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="31876-106">You can use the <xref:System.Linq.Queryable.AsQueryable%2A> method to return an <xref:System.Linq.IQueryable%601> interface from any class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="31876-107">這樣可將大部分的泛型集合類型做為資料服務的資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="31876-107">This enables most generic collection types to be used as a data source for your data service.</span></span>  
  
 <span data-ttu-id="31876-108">反映提供者支援型別階層。</span><span class="sxs-lookup"><span data-stu-id="31876-108">The reflection provider supports type hierarchies.</span></span> <span data-ttu-id="31876-109">如需詳細資訊，請參閱[How to： 建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="31876-109">For more information, see [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).</span></span>  
  
## <a name="inferring-the-data-model"></a><span data-ttu-id="31876-110">推斷資料模型</span><span class="sxs-lookup"><span data-stu-id="31876-110">Inferring the Data Model</span></span>  
 <span data-ttu-id="31876-111">當您建立資料服務時，提供者會使用反映推斷資料模型。</span><span class="sxs-lookup"><span data-stu-id="31876-111">When you create the data service, the provider infers the data model by using reflection.</span></span> <span data-ttu-id="31876-112">下列清單顯示反映提供者推斷資料模型的方式：</span><span class="sxs-lookup"><span data-stu-id="31876-112">The following list shows how the reflection provider infers the data model:</span></span>  
  
-   <span data-ttu-id="31876-113">實體容器：該類別可將資料公開為傳回 <xref:System.Linq.IQueryable%601> 執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="31876-113">Entity container - the class that exposes the data as properties that return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="31876-114">當您定址反映架構的資料模型時，實體容器代表服務的根。</span><span class="sxs-lookup"><span data-stu-id="31876-114">When you address a reflection-based data model, the entity container represents the root of the service.</span></span> <span data-ttu-id="31876-115">一個指定的命名空間僅支援一個實體容器類別。</span><span class="sxs-lookup"><span data-stu-id="31876-115">Only one entity container class is supported for a given namespace.</span></span>  
  
-   <span data-ttu-id="31876-116">實體集：傳回 <xref:System.Linq.IQueryable%601> 執行個體的屬性會被視為實體集。</span><span class="sxs-lookup"><span data-stu-id="31876-116">Entity sets - properties that return <xref:System.Linq.IQueryable%601> instances are treated as entity sets.</span></span> <span data-ttu-id="31876-117">實體集會在查詢中直接定址為資源。</span><span class="sxs-lookup"><span data-stu-id="31876-117">Entity sets are addressed directly as resources in the query.</span></span> <span data-ttu-id="31876-118">實體容器上只有一個屬性可以傳回指定型別的 <xref:System.Linq.IQueryable%601> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="31876-118">Only one property on the entity container can return an <xref:System.Linq.IQueryable%601> instance of a given type.</span></span>  
  
-   <span data-ttu-id="31876-119">實體型別：實體集所傳回之 `T` 的型別 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="31876-119">Entity types - the type `T` of the <xref:System.Linq.IQueryable%601> that the entity set returns.</span></span> <span data-ttu-id="31876-120">反映提供者會將屬於繼承階層的類別轉譯為對等的實體類型階層。</span><span class="sxs-lookup"><span data-stu-id="31876-120">Classes that are part of an inheritance hierarchy are translated by the reflection provider into an equivalent entity type hierarchy.</span></span>  
  
-   <span data-ttu-id="31876-121">實體索引鍵：每個屬於實體類型的資料類別都必須具有一個索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="31876-121">Entity keys - each data class that is an entity type must have a key property.</span></span> <span data-ttu-id="31876-122">此屬性會以 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 屬性 (`[DataServiceKeyAttribute]`) 加以屬性化。</span><span class="sxs-lookup"><span data-stu-id="31876-122">This property is attributed with the <xref:System.Data.Services.Common.DataServiceKeyAttribute> attribute (`[DataServiceKeyAttribute]`).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31876-123">您應該只將 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 屬性 (Attribute) 套用至可以用來唯一識別實體類型之執行個體的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="31876-123">You should only apply the <xref:System.Data.Services.Common.DataServiceKeyAttribute> attribute to a property that can be used to uniquely identify an instance of the entity type.</span></span> <span data-ttu-id="31876-124">此屬性 (Attribute) 在套用到導覽屬性 (Property) 時會遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="31876-124">This attribute is ignored when applied to a navigation property.</span></span>  
  
-   <span data-ttu-id="31876-125">實體類型屬性：除了實體索引鍵外，反映提供者會如下所示處理類別 (為實體類型) 的可存取非索引子屬性：</span><span class="sxs-lookup"><span data-stu-id="31876-125">Entity type properties - other than the entity key, the reflection provider treats the accessible, non-indexer properties of a class that is an entity type as follows:</span></span>  
  
    -   <span data-ttu-id="31876-126">如果屬性傳回基本型別，則會假設該屬性為實體類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="31876-126">If the property returns a primitive type, then the property is assumed to be a property of an entity type.</span></span>  
  
    -   <span data-ttu-id="31876-127">如果屬性傳回同時為實體類型的型別，則會假設該屬性為導覽屬性，代表多對一或一對一關聯性中的「一」端。</span><span class="sxs-lookup"><span data-stu-id="31876-127">If the property returns a type that is also an entity type, then the property is assumed to be a navigation property that represents the "one" end of a many-to-one or one-to-one relationship.</span></span>  
  
    -   <span data-ttu-id="31876-128">如果屬性傳回實體類型的 <xref:System.Collections.Generic.IEnumerable%601>，則會假設該屬性為導覽屬性，代表一對多或多對一關聯性中的「多」端。</span><span class="sxs-lookup"><span data-stu-id="31876-128">If the property returns an <xref:System.Collections.Generic.IEnumerable%601> of an entity type, then the property is assumed to be a navigation property that represents the "many" end of a one-to-many or many-to-many relationship.</span></span>  
  
    -   <span data-ttu-id="31876-129">如果屬性的傳回型別是實值型別，則該屬性就代表複雜類型。</span><span class="sxs-lookup"><span data-stu-id="31876-129">If the return type of the property is a value type, then the property represents a complex type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31876-130">不同於以實體關聯式模型為基礎的資料模型，以反映提供者為基礎的模型無法解譯關聯性資料。</span><span class="sxs-lookup"><span data-stu-id="31876-130">Unlike a data model that is based on the entity-relational model, models that are based on the reflection provider do not understand relational data.</span></span> <span data-ttu-id="31876-131">您應該使用 Entity Framework 透過 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 公開關聯式資料。</span><span class="sxs-lookup"><span data-stu-id="31876-131">You should use the Entity Framework to expose relational data through [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
## <a name="data-type-mapping"></a><span data-ttu-id="31876-132">資料型別對應</span><span class="sxs-lookup"><span data-stu-id="31876-132">Data Type Mapping</span></span>  
 <span data-ttu-id="31876-133">若資料模型是從 .NET Framework 類別推斷的，資料模型中的基本型別會對應至 .NET Framework 資料型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31876-133">When a data model is inferred from .NET Framework classes, the primitive types in the data model are mapped to .NET Framework data types as follows:</span></span>  
  
|<span data-ttu-id="31876-134">.NET Framework 資料型別</span><span class="sxs-lookup"><span data-stu-id="31876-134">.NET Framework data type</span></span>|<span data-ttu-id="31876-135">資料模型型別</span><span class="sxs-lookup"><span data-stu-id="31876-135">Data model type</span></span>|  
|------------------------------|---------------------|  
|<span data-ttu-id="31876-136"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="31876-136"><xref:System.Byte> `[]`</span></span>|`Edm.Binary`|  
|<xref:System.Boolean>|`Edm.Boolean`|  
|<xref:System.Byte>|`Edm.Byte`|  
|<xref:System.DateTime>|`Edm.DateTime`|  
|<xref:System.Decimal>|`Edm.Decimal`|  
|<xref:System.Double>|`Edm.Double`|  
|<xref:System.Guid>|`Edm.Guid`|  
|<xref:System.Int16>|`Edm.Int16`|  
|<xref:System.Int32>|`Edm.Int32`|  
|<xref:System.Int64>|`Edm.Int64`|  
|<xref:System.SByte>|`Edm.SByte`|  
|<xref:System.Single>|`Edm.Single`|  
|<xref:System.String>|`Edm.String`|  
  
> [!NOTE]
>  <span data-ttu-id="31876-137">.NET Framework 可為 Null 的值型別會對應至相同的資料模型類型，當成無法指派 Null 之對應值型別。</span><span class="sxs-lookup"><span data-stu-id="31876-137">.NET Framework nullable value types are mapped to the same data model types as the corresponding value types that cannot be assigned a null.</span></span>  
  
## <a name="enabling-updates-in-the-data-model"></a><span data-ttu-id="31876-138">可在資料模型中更新</span><span class="sxs-lookup"><span data-stu-id="31876-138">Enabling Updates in the Data Model</span></span>  
 <span data-ttu-id="31876-139">為允許更新透過此類資料模型公開的資料，反映提供者會定義 <xref:System.Data.Services.IUpdatable> 介面。</span><span class="sxs-lookup"><span data-stu-id="31876-139">To allow updates to data that is exposed through this kind of data model, the reflection provider defines an <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="31876-140">此介面會指示資料服務持續更新已公開型別的方法。</span><span class="sxs-lookup"><span data-stu-id="31876-140">This interface instructs the data service on how to persist updates to the exposed types.</span></span> <span data-ttu-id="31876-141">若要更新資料模型定義的資源，實體容器類別必須實作 <xref:System.Data.Services.IUpdatable> 介面。</span><span class="sxs-lookup"><span data-stu-id="31876-141">To enable updates to resources that are defined by the data model, the entity container class must implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="31876-142">如需範例實作的<xref:System.Data.Services.IUpdatable>介面，請參閱[How to： 建立使用資料服務的 LINQ to SQL 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="31876-142">For an example of an implementation of the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 <span data-ttu-id="31876-143">必須實作 <xref:System.Data.Services.IUpdatable> 介面的下列成員，才能使用反映提供者將更新傳播至資料來源。</span><span class="sxs-lookup"><span data-stu-id="31876-143">The <xref:System.Data.Services.IUpdatable> interface requires that the following members be implemented so that updates can be propagated to the data source by using the reflection provider:</span></span>  
  
|<span data-ttu-id="31876-144">成員</span><span class="sxs-lookup"><span data-stu-id="31876-144">Member</span></span>|<span data-ttu-id="31876-145">描述</span><span class="sxs-lookup"><span data-stu-id="31876-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|<span data-ttu-id="31876-146">提供將物件加入至相關物件集合的功能，該物件集合可透過導覽屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="31876-146">Provides the functionality to add an object to a collection of related objects that are accessed from a navigation property.</span></span>|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|<span data-ttu-id="31876-147">提供取消暫止資料變更的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-147">Provides the functionality that cancels pending changes to the data.</span></span>|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|<span data-ttu-id="31876-148">提供在指定容器中建立新資源的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-148">Provides the functionality to create a new resource in the specified container.</span></span>|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|<span data-ttu-id="31876-149">提供刪除資源的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-149">Provides the functionality to delete a resource.</span></span>|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|<span data-ttu-id="31876-150">提供擷取按特定查詢和型別名稱識別之資源的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-150">Provides the functionality to retrieve a resource that is identified by a specific query and type name.</span></span>|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|<span data-ttu-id="31876-151">提供傳回資源屬性值的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-151">Provides the functionality to return the value of a property of a resource.</span></span>|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|<span data-ttu-id="31876-152">提供將物件移至相關物件集合的功能，該物件集合可透過導覽屬性進行存取。</span><span class="sxs-lookup"><span data-stu-id="31876-152">Provides the functionality to remove an object to a collection of related objects accessed from a navigation property.</span></span>|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|<span data-ttu-id="31876-153">提供更新指定之資源的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-153">Provides the functionality to update a specified resource.</span></span>|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|<span data-ttu-id="31876-154">提供傳回資源的功能，該資源是由特定物件執行個體所代表。</span><span class="sxs-lookup"><span data-stu-id="31876-154">Provides the functionality to return the resource that is represented by a specific object instance.</span></span>|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|<span data-ttu-id="31876-155">提供儲存所有暫止變更的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-155">Provides the functionality to save all pending changes.</span></span>|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|<span data-ttu-id="31876-156">提供使用導覽屬性來設定相關物件參考的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-156">Provides the functionality to set a related object reference by using a navigation property.</span></span>|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|<span data-ttu-id="31876-157">提供設定資源屬性值的功能。</span><span class="sxs-lookup"><span data-stu-id="31876-157">Provides the functionality to set the value of the property of a resource.</span></span>|  
  
## <a name="handling-concurrency"></a><span data-ttu-id="31876-158">處理並行</span><span class="sxs-lookup"><span data-stu-id="31876-158">Handling Concurrency</span></span>  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="31876-159"> 支援開放式並行存取模型，其方式是讓您定義實體的並行語彙基元。</span><span class="sxs-lookup"><span data-stu-id="31876-159"> supports an optimistic concurrency model by enabling you to define a concurrency token for an entity.</span></span> <span data-ttu-id="31876-160">這個並行語彙基元包含實體的一個或多個屬性，資料服務會使用它來判斷正在要求、更新或刪除的資料中是否已經發生變更。</span><span class="sxs-lookup"><span data-stu-id="31876-160">This concurrency token, which includes one or more properties of the entity, is used by the data service to determine whether a change has occurred in the data that is being requested, updated, or deleted.</span></span> <span data-ttu-id="31876-161">當取自要求中 eTag 的語彙基元值與目前實體的值不同時，資料服務就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="31876-161">When token values obtained from the eTag in the request differ from the current values of the entity, an exception is raised by the data service.</span></span> <span data-ttu-id="31876-162"><xref:System.Data.Services.ETagAttribute> 會套用至實體類型，以便在反映提供者中定義並行語彙基元。</span><span class="sxs-lookup"><span data-stu-id="31876-162">The <xref:System.Data.Services.ETagAttribute> is applied to an entity type to define a concurrency token in the reflection provider.</span></span> <span data-ttu-id="31876-163">並行語彙基元不得包含索引鍵屬性或導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="31876-163">The concurrency token cannot include a key property or a navigation property.</span></span> <span data-ttu-id="31876-164">如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="31876-164">For more information, see [Updating the Data Service](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a><span data-ttu-id="31876-165">使用 LINQ to SQL 搭配反映提供者</span><span class="sxs-lookup"><span data-stu-id="31876-165">Using LINQ to SQL with the Reflection Provider</span></span>  
 <span data-ttu-id="31876-166">由於 Entity Framework 原本就依預設受到支援，因此在使用關聯式資料與 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 時建議使用資料提供者。</span><span class="sxs-lookup"><span data-stu-id="31876-166">Because the Entity Framework is natively supported by default, it is the recommended data provider for using relational data with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="31876-167">不過，您可以使用反映提供者來搭配使用 LINQ to SQL 類別與資料服務。</span><span class="sxs-lookup"><span data-stu-id="31876-167">However, you can use the reflection provider to use LINQ to SQL classes with a data service.</span></span> <span data-ttu-id="31876-168"><xref:System.Data.Linq.Table%601>結果集傳回的方法上<xref:System.Data.Linq.DataContext>LINQ to SQL 物件關聯式設計工具 （O/R 設計工具） 實作所產生<xref:System.Linq.IQueryable%601>介面。</span><span class="sxs-lookup"><span data-stu-id="31876-168">The <xref:System.Data.Linq.Table%601> result sets that are returned by methods on the <xref:System.Data.Linq.DataContext> generated by the LINQ to SQL Object Relational Designer (O/R Designer) implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="31876-169">這樣可讓反映提供者存取這些方法，並使用所產生的 LINQ to SQL 類別從 SQL Server 傳回實體資料。</span><span class="sxs-lookup"><span data-stu-id="31876-169">This enables the reflection provider to access these methods and return entity data from SQL Server by using the generated LINQ to SQL classes.</span></span> <span data-ttu-id="31876-170">不過，由於 LINQ to SQL 不會實作 <xref:System.Data.Services.IUpdatable> 介面，因此您需要加入部分類別以延伸現有的 <xref:System.Data.Linq.DataContext> 部分類別，來加入 <xref:System.Data.Services.IUpdatable> 實作。</span><span class="sxs-lookup"><span data-stu-id="31876-170">However, because LINQ to SQL does not implement the <xref:System.Data.Services.IUpdatable> interface, you need to add a partial class that extends the existing <xref:System.Data.Linq.DataContext> partial class to add the <xref:System.Data.Services.IUpdatable> implementation.</span></span> <span data-ttu-id="31876-171">如需詳細資訊，請參閱[How to： 建立使用資料服務的 LINQ to SQL 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="31876-171">For more information, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31876-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="31876-172">See Also</span></span>  
 [<span data-ttu-id="31876-173">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="31876-173">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
