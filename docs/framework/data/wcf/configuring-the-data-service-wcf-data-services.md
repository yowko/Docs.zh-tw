---
title: 設定資料服務 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
ms.openlocfilehash: 0824a43cba1a21cc9ae92b1f807c6a1369fd63ed
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44338931"
---
# <a name="configuring-the-data-service-wcf-data-services"></a>設定資料服務 (WCF 資料服務)
具有[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，您可以建立資料服務公開 （expose）[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要。 這些摘要中的資料可以來自各種不同的資料來源。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會使用資料提供者公開此資料，做[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要。 這些提供者包含 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供者、反映提供者，以及一組自訂資料服務提供者介面。 提供者實作會針對此服務定義資料模型。 如需詳細資訊，請參閱 <<c0> [ 資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。  
  
 在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中，資料服務是繼承自 <xref:System.Data.Services.DataService%601> 類別的一種類別，其中資料服務的類型即為資料模型的實體容器。 此實體容器具有一個或多個可傳回 <xref:System.Linq.IQueryable%601> (用於存取資料模型中的資料集) 的屬性。  
  
 資料服務的行為由 <xref:System.Data.Services.DataServiceConfiguration> 類別的成員及 <xref:System.Data.Services.DataServiceBehavior> 類別的成員定義，可從 <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> 類別的 <xref:System.Data.Services.DataServiceConfiguration> 屬性存取。 <xref:System.Data.Services.DataServiceConfiguration> 類別會提供給資料服務所實作的 `InitializeService` 方法，如下列 Northwind 資料服務實作所示：  
  
[!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/Astoria Northwind Service/cs/northwind.svc.cs#dataserviceconfigcomplete)]  
[!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/Astoria Northwind Service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## <a name="data-service-configuration-settings"></a>資料服務組態設定  
 <xref:System.Data.Services.DataServiceConfiguration> 類別可讓您指定下列資料服務行為：  
  
|成員|行為|  
|------------|--------------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|可讓您使用 `$count` 路徑區段和 `$inlinecount` 查詢選項，停用送出至資料服務的計數要求。 如需詳細資訊，請參閱 < [OData: URI 慣例](https://go.microsoft.com/fwlink/?LinkId=185564)。|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|可讓您使用 `$select` 查詢選項，在提交至資料服務的要求中停用資料保護的支援。 如需詳細資訊，請參閱 < [OData: URI 慣例](https://go.microsoft.com/fwlink/?LinkId=185564)。|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|可讓您在中繼資料中公開使用 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面定義之動態中繼資料提供者的資料類型。|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|可讓您指定資料服務執行階段是否應將包含在承載中的類型，轉換成要求所指定的實際屬性類型。|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|可讓您指定是否要在刪除兩個實體間的關聯性時，叫用註冊的變更攔截器。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|可讓您限制單一批次中允許的變更集與查詢作業數目。 如需詳細資訊，請參閱 < [OData： 批次](https://go.microsoft.com/fwlink/?LinkId=185602)並[批次作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|可讓您限制單一變更集中包含的變更次數。 如需詳細資訊，請參閱 <<c0> [ 如何： 啟用分頁的資料服務結果](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|可讓您使用 `$expand` 查詢運算子限制包含在單一要求中的相關實體數目，進而限制回應的大小。 如需詳細資訊，請參閱 < 請參閱[OData: URI 慣例](https://go.microsoft.com/fwlink/?LinkId=185564)並[載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|可讓您使用 `$expand` 查詢運算子限制包含在單一要求中的相關實體圖形深度，進而限制回應的大小。 如需詳細資訊，請參閱 < 請參閱[OData: URI 慣例](https://go.microsoft.com/fwlink/?LinkId=185564)並[載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|可讓您限制單一 POST 要求中可包含及插入的實體數目。|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|定義資料服務所使用的 Atom 通訊協定版本。 當 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> 的值設定為小於 <xref:System.Data.Services.Common.DataServiceProtocolVersion> 的最大值時，存取資料服務的用戶端就無法使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 的最新功能。 如需詳細資訊，請參閱 <<c0> [ 資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|可讓您限制以資料摘要傳回之每個實體集中的實體數目來限制回應的大小。|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|將資料型別加入至按資料服務辨識的型別清單。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|設定資料服務中可用之實體集資源的存取權限。 可提供星號 (`*`) 值給名稱參數，將所有剩餘實體集的存取權限設為相同層級。 建議您設定實體集的存取權，以提供最少權限來存取用戶端應用程式所需的資料服務資源。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。 例如指定的 URI 和 HTTP 動作所需的最小存取權限的詳細資訊，請參閱中的資料表[最小的資源存取需求](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements)一節。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|設定實體集資源的最大頁面大小。 如需詳細資訊，請參閱 <<c0> [ 如何： 啟用分頁的資料服務結果](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|設定在資料服務中定義的服務作業存取權限。 如需詳細資訊，請參閱 <<c0> [ 服務作業](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)。 可提供星號 (`*`) 值給名稱參數，將所有服務作業的存取權限設為相同層級。 建議您設定服務作業的存取權限，以提供最少權限給用戶端應用程式所需的資料服務資源。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|此組態屬性可讓您在錯誤回應訊息中傳回詳細資訊，更加輕鬆地疑難排解資料服務問題。 此選項不適用於實際執行環境。 如需詳細資訊，請參閱 <<c0> [ 開發和部署 WCF Data Services](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)。|  
  
<a name="accessRequirements"></a>   
## <a name="minimum-resource-access-requirements"></a>最少資源存取需求  
 下表詳述為了執行特定作業所必須授與的最少實體集權限。 路徑範例以 Northwind 資料服務，當您完成時，不僅[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。 因為 <xref:System.Data.Services.EntitySetRights> 列舉和 <xref:System.Data.Services.ServiceOperationRights> 列舉的定義方式是使用 <xref:System.FlagsAttribute> 所定義，所以您可以使用邏輯 OR 運算子為單一實體集或作業指定多個權限。 如需詳細資訊，請參閱 <<c0> [ 如何： 啟用資料服務的存取](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)。  
  
|路徑/動作|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|------------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|不支援|不支援|<xref:System.Data.Services.EntitySetRights.WriteAppend>|不支援|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge>|N/A|<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|不支援|不支援|`Customers`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge> 或 <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> -和-<br /><br /> `Orders` `:` 和 <xref:System.Data.Services.EntitySetRights.WriteAppend>|不支援|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteDelete>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge>|不支援|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteDelete><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge>；<br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend><br /><br /> -和-<br /><br /> `Orders`：<xref:System.Data.Services.EntitySetRights.WriteAppend> 和 <xref:System.Data.Services.EntitySetRights.ReadSingle>|不支援|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|不支援|不支援|`Customers`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge> 或 <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|不支援|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge> 或 <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|不支援|不支援|不支援|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Orders`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge> 或 <xref:System.Data.Services.EntitySetRights.WriteReplace>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteMerge>|不支援|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle>;<br /><br /> -和-<br /><br /> `Orders`：<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|不支援|不支援|不支援|不支援|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|不支援|<xref:System.Data.Services.EntitySetRights.WriteMerge>|不支援|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value` <sup>1</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.WriteDelete>|不支援|不支援|不支援|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> 和 <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.WriteMerge>|不支援|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/$value` <sup>2</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|不支援|不支援|不支援|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|不支援|不支援|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend>|不支援|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> -和-<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|不支援|不支援|不支援|不支援|  
  
 <sup>1</sup>在此範例中，`Address`表示複雜型別屬性`Customers`具有名為屬性的實體`StreetAddress`。 Northwind 資料服務所使用的模型不會明確定義這個複雜類型。 當此資料模型是使用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 提供者所定義時，您可以使用 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 工具來定義這類複雜類型。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立和修改複雜型別](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d)。  
  
 <sup>2</sup>傳回二進位大型物件 (BLOB) 的屬性定義與媒體資源屬於媒體連結項目，在此情況下，實體時，這個 URI 支援`Customers`。 如需詳細資訊，請參閱 <<c0> [ 資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>版本控制需求  
 下列資料服務組態行為需要 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定第 2 版或更新版本：  
  
-   計數要求的支援。  
  
-   用於投影之 $select 查詢選項的支援。  
  
 如需詳細資訊，請參閱 <<c0> [ 資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [裝載資料服務](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
