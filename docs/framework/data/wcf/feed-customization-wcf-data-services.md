---
title: 自訂摘要 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
ms.openlocfilehash: b4ea05b0112af4c1dcb6308a08ab3b31c586fbe8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790860"
---
# <a name="feed-customization-wcf-data-services"></a>自訂摘要 (WCF 資料服務)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]會使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]將資料公開為摘要。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]支援資料摘要的 Atom 和 JavaScript 物件標記法（JSON）格式。 當您使用 Atom 摘要時， [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]會提供標準的方法，將資料（例如實體和關聯性）序列化為 XML 格式，以包含在 HTTP 訊息的主體中。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]定義實體和 Atom 元素中所包含之資料之間的預設實體屬性對應。 如需詳細資訊， [請參閱 OData：Atom 格式](https://go.microsoft.com/fwlink/?LinkID=185794)。  
  
 您可能有一個應用程式案例，該案例要求資料服務所傳回的屬性資料是以自訂行為序列化，而不是以標準摘要格式序列化。 使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]，您可以自訂資料摘要中的序列化，讓實體的屬性可以對應至專案的未使用元素和屬性，或饋送中專案的自訂元素。  
  
> [!NOTE]
> 僅支援 Atom 摘要的摘要自訂。 當傳回的摘要需要 JSON 格式時，不會傳回自訂摘要。  
  
 透過 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，您可以手動將屬性套用至資料模型中的實體類型，藉以定義 Atom 裝載的替代實體屬性對應。 資料服務的資料來源提供者會判斷您應如何套用這些屬性。  
  
> [!IMPORTANT]
> 當您定義自訂摘要時，您必須確保所有已定義自訂對應的實體屬性都包含在投影中。 若投影中未包含對應的實體屬性，則可能會發生資料遺失。 如需詳細資訊，請參閱[查詢投影](query-projections-wcf-data-services.md)。  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>使用 Entity Framework 提供者自訂摘要  
 搭配 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供者使用的資料模型在 .edmx 檔案中以 XML 表示。 在這種情況下，定義自訂摘要的屬性會新增至 `EntityType` 和`Property` 項目，表示資料模型中的實體類型和屬性。 這些摘要自訂屬性未定義于[MC-CSDL\]中\[：概念結構定義檔案格式](https://go.microsoft.com/fwlink/?LinkId=159072)，這是[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]提供者用來定義資料模型的格式。 因此，您必須在特定的結構描述命名空間中宣告摘要自訂屬性，定義為 `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`。 下列 XML 片段會顯示套用至 `Property` 實體類型之 `Products` 項目的摘要自訂屬性，定義 `ProductName`、`ReorderLevel` 和 `UnitsInStock` 屬性。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 這些屬性會針對 `Products` 實體集產生下列自訂資料摘要。 在自訂資料摘要中，`ProductName` 屬性 (property) 值會同時顯示在 `author` 項目中並做為 `ProductName` 屬性 (property) 項目，而 `UnitsInStock` 屬性 (property) 則會顯示在自訂項目中，它具有其唯一的命名空間和做為屬性 (attribute) 的 `ReorderLevel` 屬性 (property)：  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 如需詳細資訊，請參閱[如何：使用 Entity Framework 提供者](how-to-customize-feeds-with-ef-provider-wcf-data-services.md)自訂摘要。  
  
> [!NOTE]
> 由於 Entity Designer 不支援資料模型的副檔名，您必須手動修改包含資料模型的 XML 檔案。 如需實體資料模型工具所產生之 .edmx 檔案的詳細資訊，請參閱 .edmx 檔案[總覽（Entity Framework）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))。  
  
### <a name="custom-feed-attributes"></a>自訂摘要屬性  
 下表顯示可自訂摘要的 XML 屬性，您可以將它們加入至定義資料模型的概念結構定義語言 (CSDL) 中。 這些屬性 (Attribute) 相當於搭配反映提供者所使用之 <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> 的屬性 (Property)。  
  
|屬性名稱|描述|  
|--------------------|-----------------|  
|`FC_ContentKind`|指示內容的類型。 以下關鍵字可定義新聞訂閱方式內容類型。<br /><br /> `text:`屬性值在摘要中會顯示為文字。<br /><br /> `html:`屬性值在摘要中會顯示為 HTML。<br /><br /> `xhtml:`屬性值在摘要中會顯示為 XML 格式的 HTML。<br /><br /> 這些關鍵字相當於搭配反映提供者所使用之 <xref:System.Data.Services.Common.SyndicationTextContentKind> 列舉的值。<br /><br /> 使用 `FC_NsPrefix` 和 `FC_NsUri` 屬性時，將不支援此屬性。<br /><br /> 在您指定 `xhtml` 屬性的`FC_ContentKind` 值時，必須先確保屬性值會包含格式正確的 XML。 資料服務會傳回未執行任何轉換的值。 您還必須確保傳回之 XML 中的任何 XML 項目前置詞具備命名空間 URI 以及對應之摘要中所定義的前置詞。|  
|`FC_KeepInContent`|指出參考的屬性值應包含在摘要的內容區段以及所對應的位置中。 有效值為 `true` 和 `false`。 若要讓產生的摘要與舊版[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]回溯相容，請指定的`true`值，以確定此值包含在摘要的內容區段中。|  
|`FC_NsPrefix`|非新聞訂閱方式對應中 XML 項目的命名空間前置詞。 這個屬性必須搭配 `FC_NsUri` 屬性使用，不能搭配 `FC_ContentKind` 屬性使用。|  
|`FC_NsUri`|非新聞訂閱方式對應中 XML 項目的命名空間 URI。 這個屬性必須搭配 `FC_NsPrefix` 屬性使用，不能搭配 `FC_ContentKind` 屬性使用。|  
|`FC_SourcePath`|此摘要對應規則套用的實體屬性路徑。 僅支援用於 `EntityType` 項目中的屬性。<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> 屬性不能直接參考複雜型別。 針對複雜型別，您必須使用路徑運算式，其中的屬性名稱以反斜線 (`/`) 字元隔開。 例如，具有 integer 屬性`Person` `Age`和複雜屬性的實體類型允許下列值<br /><br /> `Address`：<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> 屬性不能設為包含空格或其他字元的值，這些在屬性名稱中不是有效字元。|  
|`FC_TargetPath`|對應屬性之結果摘要的目標項目名稱。 這個項目可以是元素規格定義的項目或自訂項目。<br /><br /> 以下關鍵字是預先定義的新聞訂閱方式目標路徑值，指向 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要中的特定位置。<br /><br /> `SyndicationAuthorEmail:``atom:author`元素`atom:email`的子項目。<br /><br /> `SyndicationAuthorName:``atom:author`元素`atom:name`的子項目。<br /><br /> `SyndicationAuthorUri:``atom:author`元素`atom:uri`的子項目。<br /><br /> `SyndicationContributorEmail:``atom:contributor`元素`atom:email`的子項目。<br /><br /> `SyndicationContributorName:``atom:contributor`元素`atom:name`的子項目。<br /><br /> `SyndicationContributorUri:``atom:contributor`元素`atom:uri`的子項目。<br /><br /> `SyndicationCustomProperty:`自訂屬性元素。 對應至自訂項目時，目標必須是路徑運算式，其中巢狀項目以反斜線 (`/`) 隔開，而且屬性以連字號 (`@`) 指定。 下列範例中，字串 `UnitsInStock/@ReorderLevel` 將屬性值對應至名為 `ReorderLevel` 的屬性，位於根項目中名為 `UnitsInStock` 的子項目之上。<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> 當目標是自訂項目名稱時，也必須指定 `FC_NsPrefix` 和 `FC_NsUri` 屬性。<br /><br /> `SyndicationPublished:``atom:published`元素。<br /><br /> `SyndicationRights:``atom:rights`元素。<br /><br /> `SyndicationSummary:``atom:summary`元素。<br /><br /> `SyndicationTitle:``atom:title`元素。<br /><br /> `SyndicationUpdated:``atom:updated`元素。<br /><br /> 這些關鍵字相當於搭配反映提供者所使用之 <xref:System.Data.Services.Common.SyndicationItemProperty> 列舉的值。|  
  
> [!NOTE]
> 屬性名稱和值需區分大小寫。 屬性可套用至 `EntityType` 項目或一個或多個 `Property` 項目，但不能同時套用至兩者。  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>使用反映提供者自訂摘要  
 若要自訂使用反映提供者所實作之自訂資料模型的摘要時，將一個或多個 <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> 屬性的執行個體新增至類別中，該類別表示資料模型中的實體類型。 對應至摘要自訂屬性之 <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> 類別的屬性已在上一節中說明。 以下範例是 `Order` 型別的宣告，包含針對兩個屬性定義的自訂摘要對應。  
  
> [!NOTE]
> 此範例的資料模型定義于[how to：使用反映提供者](create-a-data-service-using-rp-wcf-data-services.md)建立資料服務。  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 這些屬性會針對 `Orders` 實體集產生下列自訂資料摘要。 在此自訂摘要中`OrderId` ，屬性值只會顯示`title`在的`Customer`元素`entry`中，而屬性值會同時顯示`author`在專案和`Customer`屬性專案中：  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 如需詳細資訊，請參閱[如何：使用反映提供者](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md)自訂摘要。  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>使用自訂資料服務提供者自訂摘要  
 如果要針對某個資源類型定義使用自訂資料服務提供者所定義之資料模型的摘要自訂，請在表示資料模型中實體類型的 <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> 上呼叫 <xref:System.Data.Services.Providers.ResourceType>。 如需詳細資訊，請參閱[自訂資料服務提供者](custom-data-service-providers-wcf-data-services.md)。  
  
## <a name="consuming-custom-feeds"></a>使用自訂摘要  
 當您的應用程式直接[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]取用摘要時，它必須能夠處理傳回之摘要中的任何自訂元素和屬性。 當您已在資料模型中實作自訂摘要時，無論資料服務提供者為何，`$metadata` 端點都會傳回自訂摘要資訊，如同資料服務傳回 CSDL 中的自訂摘要屬性。 當您使用 [**加入服務參考**] 對話方塊或[datasvcutil](wcf-data-service-client-utility-datasvcutil-exe.md)工具來產生用戶端資料服務類別時，會使用自訂的摘要屬性，以確保正確處理資料服務的要求和回應。  
  
## <a name="feed-customization-considerations"></a>摘要自訂考量  
 定義自訂摘要對應時，您應該考慮下列事項。  
  
- 當[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]摘要中只包含空白字元時，用戶端會將摘要中的對應元素視為空白。 因此，只包含空白字元的對應元素不會在具有相同空白字元的用戶端上具體化。 若要保留用戶端上的這個空白字元，您必須在摘要對應`KeepInContext`屬性`true`中，將的值設定為。  
  
## <a name="versioning-requirements"></a>版本控制需求  
 摘要自訂具有下列 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定版本控制需求：  
  
- 摘要自訂要求用戶端和資料服務都支援 2.0 版的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定和更新版本。  
  
 如需詳細資訊，請參閱[資料服務版本](data-service-versioning-wcf-data-services.md)設定。  
  
## <a name="see-also"></a>另請參閱

- [反映提供者](reflection-provider-wcf-data-services.md)
- [Entity Framework 提供者](entity-framework-provider-wcf-data-services.md)
