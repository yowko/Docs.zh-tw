---
title: 查詢投影 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 2e4c40d6c71a254d5f40ea42788608e10c5872a7
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517170"
---
# <a name="query-projections-wcf-data-services"></a><span data-ttu-id="6fbcd-102">查詢投影 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="6fbcd-102">Query Projections (WCF Data Services)</span></span>

<span data-ttu-id="6fbcd-103">投影提供一種機制，在[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]減少，僅傳回特定屬性的實體會在回應中藉由指定查詢所傳回之摘要中的資料量。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-103">Projection provides a mechanism in the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to reduce the amount of data in the feed returned by a query by specifying that only certain properties of an entity are returned in the response.</span></span> <span data-ttu-id="6fbcd-104">如需詳細資訊，請參閱[OData:選取系統查詢選項 ($select)](https://go.microsoft.com/fwlink/?LinkId=186076)。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-104">For more information, see [OData: Select System Query Option ($select)](https://go.microsoft.com/fwlink/?LinkId=186076).</span></span>

<span data-ttu-id="6fbcd-105">本主題描述如何定義查詢投影、實體與非實體類型的需求為何、對投影結果進行更新、建立投影類型，以及列出一些投影考量因素。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-105">This topic describes how to define a query projection, what the requirements are for entity and non-entity types, making updates to projected results, creating projected types, and lists some projection considerations.</span></span>

## <a name="defining-a-query-projection"></a><span data-ttu-id="6fbcd-106">定義查詢投影</span><span class="sxs-lookup"><span data-stu-id="6fbcd-106">Defining a Query Projection</span></span>

<span data-ttu-id="6fbcd-107">您可以將投影子句加入查詢藉由使用`$select`查詢選項在 URI 中或使用[選取](~/docs/csharp/language-reference/keywords/select-clause.md)子句 ([選取](~/docs/visual-basic/language-reference/queries/select-clause.md)Visual Basic 中) 中的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-107">You can add a projection clause to a query either by using the `$select` query option in a URI or by using the [select](~/docs/csharp/language-reference/keywords/select-clause.md) clause ([Select](~/docs/visual-basic/language-reference/queries/select-clause.md) in Visual Basic) in a LINQ query.</span></span> <span data-ttu-id="6fbcd-108">傳回的實體資料可以投影至用戶端上的實體類型或非實體類型。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-108">Returned entity data can be projected into either entity types or non-entity types on the client.</span></span> <span data-ttu-id="6fbcd-109">此主題中的範例將示範如何在 LINQ 查詢中使用 `select` 子句。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-109">Examples in this topic demonstrate how to use the `select` clause in a LINQ query.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fbcd-110">當您儲存對投影類型所進行的更新時，資料服務中可能會遺失資料。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-110">Data loss might occur in the data service when you save updates that were made to projected types.</span></span> <span data-ttu-id="6fbcd-111">如需詳細資訊，請參閱 <<c0> [ 投影考量因素](#considerations)。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-111">For more information, see [Projection Considerations](#considerations).</span></span>

## <a name="requirements-for-entity-and-non-entity-types"></a><span data-ttu-id="6fbcd-112">實體與非實體類型的需求</span><span class="sxs-lookup"><span data-stu-id="6fbcd-112">Requirements for Entity and Non-Entity Types</span></span>

<span data-ttu-id="6fbcd-113">實體類型必須具備一個或多個構成實體索引鍵的識別屬性。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-113">Entity types must have one or more identity properties that make up the entity key.</span></span> <span data-ttu-id="6fbcd-114">實體類型在用戶端上是利用下列其中一種方式來定義：</span><span class="sxs-lookup"><span data-stu-id="6fbcd-114">Entity types are defined on clients in one of the following ways:</span></span>

- <span data-ttu-id="6fbcd-115">將 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 或 <xref:System.Data.Services.Common.DataServiceEntityAttribute> 套用至類型。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-115">By applying the <xref:System.Data.Services.Common.DataServiceKeyAttribute> or <xref:System.Data.Services.Common.DataServiceEntityAttribute> to the type.</span></span>

- <span data-ttu-id="6fbcd-116">當類型具有名為 `ID` 的屬性時。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-116">When the type has a property named `ID`.</span></span>

- <span data-ttu-id="6fbcd-117">當類型具有名為*型別*`ID`，其中*類型*是類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-117">When the type has a property named *type*`ID`, where *type* is the name of the type.</span></span>

<span data-ttu-id="6fbcd-118">根據預設，當您將查詢結果投影至用戶端上定義的類型時，投影中要求的屬性必須是用戶端上現有的類型。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-118">By default, when you project query results into a type defined at the client, the properties requested in the projection must exist in the client type.</span></span> <span data-ttu-id="6fbcd-119">但是，當您為 `true` 的 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 屬性指定 <xref:System.Data.Services.Client.DataServiceContext> 值時，投影中指定的屬性就不一定要用戶端上現有的類型。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-119">However, when you specify a value of `true` for the <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> property of the <xref:System.Data.Services.Client.DataServiceContext>, properties specified in the projection are not required to occur in the client type.</span></span>

### <a name="making-updates-to-projected-results"></a><span data-ttu-id="6fbcd-120">對投影結果進行更新</span><span class="sxs-lookup"><span data-stu-id="6fbcd-120">Making Updates to Projected Results</span></span>

<span data-ttu-id="6fbcd-121">若已呼叫 <xref:System.Data.Services.Client.DataServiceContext> 方法，當您將查詢結果投影至用戶端上的實體類型時，<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 可以使用要傳送回資料服務的更新來追蹤該些物件。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-121">When you project query results into entity types on the client, the <xref:System.Data.Services.Client.DataServiceContext> can track those objects with updates to be sent back to the data service when the <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> method is called.</span></span> <span data-ttu-id="6fbcd-122">但是，對投影至用戶端上之非實體類型的資料所進行之更新，無法傳送回資料服務。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-122">However, updates that are made to data projected into non-entity types on the client cannot be sent back to the data service.</span></span> <span data-ttu-id="6fbcd-123">這是因為沒有索引鍵可識別實體執行個體，資料服務無法更新資料來源中的正確實體。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-123">This is because without a key to identify the entity instance, the data service cannot update the correct entity in the data source.</span></span> <span data-ttu-id="6fbcd-124">非實體類型並未附加至 <xref:System.Data.Services.Client.DataServiceContext>。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-124">Non-entity types are not attached to the <xref:System.Data.Services.Client.DataServiceContext>.</span></span>

<span data-ttu-id="6fbcd-125">當資料服務中所定義之實體類型的一個或多個屬性並不存在實體所投影至的用戶端類型中時，插入新的實體並不會包含這些遺漏的屬性。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-125">When one or more properties of an entity type defined in the data service do not occur in the client type into which the entity is projected, inserts of new entities will not contain these missing properties.</span></span> <span data-ttu-id="6fbcd-126">在此情況下，將會對現有實體的更新**也**不包含這些遺漏的屬性。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-126">In this case, updates that are made to existing entities will **also** not include these missing properties.</span></span> <span data-ttu-id="6fbcd-127">若此類屬性中已存有值，更新會依資料來源中所定義，將它重設為屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-127">When a value exists for such a property, the update resets it to the default value for the property, as defined in the data source.</span></span>

### <a name="creating-projected-types"></a><span data-ttu-id="6fbcd-128">建立投影類型</span><span class="sxs-lookup"><span data-stu-id="6fbcd-128">Creating Projected Types</span></span>

<span data-ttu-id="6fbcd-129">下列範例使用匿名 LINQ 查詢，將 `Customers` 類型的地址相關屬性投影至新的 `CustomerAddress` 類型，後者類型已在用戶端上定義並屬性化為實體類型：</span><span class="sxs-lookup"><span data-stu-id="6fbcd-129">The following example uses an anonymous LINQ query that projects the address-related properties of the `Customers` type into a new `CustomerAddress` type, which is defined on the client and is attributed as an entity type:</span></span>

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

<span data-ttu-id="6fbcd-130">在此範例中，物件初始設定式模式會用來建立 `CustomerAddress` 類型的新執行個體，而非用來呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-130">In this example, the object initializer pattern is used to create a new instance of the `CustomerAddress` type instead of calling a constructor.</span></span> <span data-ttu-id="6fbcd-131">在投影至實體類型時不支援建構函式，但是投影至非實體與匿名型別時可以使用建構函式。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-131">Constructors are not supported when projecting into entity types, but they can be used when projecting into non-entity and anonymous types.</span></span> <span data-ttu-id="6fbcd-132">因為 `CustomerAddress` 是實體類型，所以可以進行變更並將變更傳送回資料服務。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-132">Because `CustomerAddress` is an entity type, changes can be made and sent back to the data service.</span></span>

<span data-ttu-id="6fbcd-133">而且，取自 `Customer` 類型的資料是投影至 `CustomerAddress` 實體類型的執行個體，而非投影至匿名型別。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-133">Also, the data from the `Customer` type is projected into an instance of the `CustomerAddress` entity type instead of an anonymous type.</span></span> <span data-ttu-id="6fbcd-134">可支援投影至匿名型別，但是因為匿名型別被視為非實體類型，所以資料是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-134">Projection into anonymous types is supported, but the data is read-only because anonymous types are treated as non-entity types.</span></span>

<span data-ttu-id="6fbcd-135"><xref:System.Data.Services.Client.MergeOption> 的 <xref:System.Data.Services.Client.DataServiceContext> 設定可在查詢投影期間供識別解析使用。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-135">The <xref:System.Data.Services.Client.MergeOption> settings of the <xref:System.Data.Services.Client.DataServiceContext> are used for identity resolution during query projection.</span></span> <span data-ttu-id="6fbcd-136">這表示如果 `Customer` 中已有 <xref:System.Data.Services.Client.DataServiceContext> 類型的執行個體，使用相同識別之 `CustomerAddress` 的執行個體將會依照 <xref:System.Data.Services.Client.MergeOption> 所設定的識別解析規則</span><span class="sxs-lookup"><span data-stu-id="6fbcd-136">This means that if an instance of the `Customer` type already exists in the <xref:System.Data.Services.Client.DataServiceContext>, an instance of `CustomerAddress` with the same identity will follow the identity resolution rules set by the <xref:System.Data.Services.Client.MergeOption></span></span>

<span data-ttu-id="6fbcd-137">以下描述將結果投影至實體與非實體類型時的行為：</span><span class="sxs-lookup"><span data-stu-id="6fbcd-137">The following describes the behaviors when projecting results into entity and non-entity types:</span></span>

<span data-ttu-id="6fbcd-138">**使用初始設定式建立新的投影執行個體**</span><span class="sxs-lookup"><span data-stu-id="6fbcd-138">**Creating a new projected instance by using initializers**</span></span>

- <span data-ttu-id="6fbcd-139">範例：</span><span class="sxs-lookup"><span data-stu-id="6fbcd-139">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- <span data-ttu-id="6fbcd-140">實體類型：支援</span><span class="sxs-lookup"><span data-stu-id="6fbcd-140">Entity type: Supported</span></span>

- <span data-ttu-id="6fbcd-141">非實體類型：支援</span><span class="sxs-lookup"><span data-stu-id="6fbcd-141">Non-entity type: Supported</span></span>

<span data-ttu-id="6fbcd-142">**使用建構函式，以建立新的投影執行個體**</span><span class="sxs-lookup"><span data-stu-id="6fbcd-142">**Creating a new projected instance by using constructors**</span></span>

- <span data-ttu-id="6fbcd-143">範例：</span><span class="sxs-lookup"><span data-stu-id="6fbcd-143">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- <span data-ttu-id="6fbcd-144">實體類型：引發 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-144">Entity type: A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="6fbcd-145">非實體類型：支援</span><span class="sxs-lookup"><span data-stu-id="6fbcd-145">Non-entity type: Supported</span></span>

<span data-ttu-id="6fbcd-146">**使用投影來轉換屬性值**</span><span class="sxs-lookup"><span data-stu-id="6fbcd-146">**Using projection to transform a property value**</span></span>

- <span data-ttu-id="6fbcd-147">範例：</span><span class="sxs-lookup"><span data-stu-id="6fbcd-147">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- <span data-ttu-id="6fbcd-148">實體類型：實體類型不支援此種轉換，因為它可能造成混淆且可能覆寫屬於另一個實體之資料來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-148">Entity type: This transformation is not supported for entity types because it can lead to confusion and potentially overwriting the data in the data source that belongs to another entity.</span></span> <span data-ttu-id="6fbcd-149">引發 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-149">A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="6fbcd-150">非實體類型：支援</span><span class="sxs-lookup"><span data-stu-id="6fbcd-150">Non-entity type: Supported</span></span>

<a name="considerations"></a>

## <a name="projection-considerations"></a><span data-ttu-id="6fbcd-151">投影考量因素</span><span class="sxs-lookup"><span data-stu-id="6fbcd-151">Projection Considerations</span></span>

<span data-ttu-id="6fbcd-152">下列其他考量因素適用於定義查詢投影時。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-152">The following additional considerations apply when defining a query projection.</span></span>

- <span data-ttu-id="6fbcd-153">在定義 Atom 格式的自訂摘要時，您必須確保所有已定義自訂對應的實體屬性都包含在投影中。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-153">When you define custom feeds for the Atom format, you must make sure that all entity properties that have custom mappings defined are included in the projection.</span></span> <span data-ttu-id="6fbcd-154">若投影中未包含對應的實體屬性，則可能會發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-154">When a mapped entity property is not included in the projection, data loss might occur.</span></span> <span data-ttu-id="6fbcd-155">如需詳細資訊，請參閱 <<c0> [ 摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-155">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>

- <span data-ttu-id="6fbcd-156">對未包含資料服務之資料模型中的所有實體屬性之投影類型進行插入時，用戶端上未包含在投影內的屬性會設定為它們的預設值。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-156">When inserts are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, the properties not included in the projection at the client are set to their default values.</span></span>

- <span data-ttu-id="6fbcd-157">對未包含資料服務之資料模型中的所有實體屬性之投影類型進行更新時，用戶端上未包含在投影內的現有值將被覆寫成未初始化的預設值。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-157">When updates are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, existing values not included in the projection on the client will be overwritten with uninitialized default values.</span></span>

- <span data-ttu-id="6fbcd-158">當投影包括一種複雜屬性時，必須傳回整個複雜物件。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-158">When a projection includes a complex property, the entire complex object must be returned.</span></span>

- <span data-ttu-id="6fbcd-159">當投影包含導覽屬性時，相關物件會以隱含方式載入，不必呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-159">When a projection includes a navigation property, the related objects are loaded implicitly without having to call the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method.</span></span> <span data-ttu-id="6fbcd-160">不支援將 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法用於投影查詢中。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-160">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is not supported for use in a projected query.</span></span>

- <span data-ttu-id="6fbcd-161">查詢用戶端上的投影查詢會轉譯為在要求 URI 中使用 `$select` 查詢選項。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-161">Query projections queries on the client are translated to use the `$select` query option in the request URI.</span></span> <span data-ttu-id="6fbcd-162">若針對舊版 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 執行使用投影的查詢 (該版本不支援 `$select` 查詢選項)，會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-162">When a query with projection is executed against a previous version of [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] that does not support the `$select` query option, an error is returned.</span></span> <span data-ttu-id="6fbcd-163">在將資料服務之 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> 的 <xref:System.Data.Services.DataServiceBehavior> 設定為 <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1> 值時也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-163">This can also happen when the <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> of the <xref:System.Data.Services.DataServiceBehavior> for the data service is set to a value of <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>.</span></span> <span data-ttu-id="6fbcd-164">如需詳細資訊，請參閱 <<c0> [ 資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-164">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span>

<span data-ttu-id="6fbcd-165">如需詳細資訊，請參閱[如何：將查詢結果投影](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6fbcd-165">For more information, see [How to: Project Query Results](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6fbcd-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fbcd-166">See also</span></span>

- [<span data-ttu-id="6fbcd-167">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="6fbcd-167">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
