---
title: 匯出和匯入中繼資料
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 692382de81459ad52d306ca7fd05546b4e36294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963671"
---
# <a name="exporting-and-importing-metadata"></a>匯出和匯入中繼資料
在 Windows Communication Foundation (WCF) 中, 匯出中繼資料是描述服務端點並將其投射至平行、標準化標記法的程式, 用戶端可用來瞭解如何使用服務。 匯入服務中繼資料是從服務中繼資料產生 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體或組件的程序。  
  
## <a name="exporting-metadata"></a>匯出中繼資料  
 若要從 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 執行個體匯出中繼資料，請使用 <xref:System.ServiceModel.Description.MetadataExporter> 抽象類別的實作。 型別是包含在 WCF 中<xref:System.ServiceModel.Description.MetadataExporter>的抽象類別的執行。 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> 型別會使用在 <xref:System.ServiceModel.Description.MetadataSet> 執行個體中封裝的附加原則運算式來產生 Web 服務描述語言 (WSDL) 中繼資料。 您可以使用 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> 執行個體來反覆匯出 <xref:System.ServiceModel.Description.ContractDescription> 物件和 <xref:System.ServiceModel.Description.ServiceEndpoint> 物件的中繼資料。 您也可以匯出 <xref:System.ServiceModel.Description.ServiceEndpoint> 物件的集合，並將之與特定服務名稱進行關聯。  
  
> [!NOTE]
> 您只能使用 `WsdlExporter` 從包含 Common Language Runtime (CLR) 型別資訊的 `ContractDescription` 執行個體中匯出中繼資料，例如透過 `ContractDescription` 方法建立的 `ContractDescription.GetContract` 執行個體，或是建立為 `ServiceDescription` 執行個體的 `ServiceHost` 一部分。 對於從服務中繼資料匯入或是未使用型別資訊建構的 `WsdlExporter` 執行個體，則無法使用 `ContractDescription` 從這類執行個體匯出中繼資料。  
  
## <a name="importing-metadata"></a>匯入中繼資料  
  
### <a name="importing-wsdl-documents"></a>匯入 WSDL 文件  
 若要在 WCF 中匯入服務中繼資料, 請<xref:System.ServiceModel.Description.MetadataImporter>使用抽象類別的執行。 型別是包含在 WCF 中<xref:System.ServiceModel.Description.MetadataImporter>的抽象類別的執行。 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> <xref:System.ServiceModel.Description.WsdlImporter> 型別會匯入 WSDL 中繼資料，其中包含與 <xref:System.ServiceModel.Description.MetadataSet> 物件組合在一起的附加原則。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> 型別可讓您控制匯入中繼資料的方式。 您可以匯入所有端點、所有繫結或是所有合約。 您可以匯入與特定 WSDL 服務、繫結或連接埠類型相關聯的所有端點。 您也可以匯入特定 WSDL 連接埠的端點、特定 WSDL 繫結的繫結，或是特定 WSDL 連接埠類型的合約。  
  
 同時，<xref:System.ServiceModel.Description.WsdlImporter> 會公開 <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> 屬性，讓您指定不需要匯入的合約集。 <xref:System.ServiceModel.Description.WsdlImporter> 會使用 <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> 屬性中的合約，而不是匯入合約 (內含來自中繼資料的相同限定名稱)。  
  
### <a name="importing-policies"></a>匯入原則  
 <xref:System.ServiceModel.Description.WsdlImporter> 型別會收集附加至訊息、作業與端點原則主體的原則運算式，然後使用 <xref:System.ServiceModel.Description.IPolicyImportExtension> 集合中的 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> 實作來匯入原則運算式。  
  
 原則匯入邏輯會自動處理位於相同 WSDL 文件中的原則運算式之原則參考，並使用 `wsu:Id` 或 `xml:id` 屬性加以識別。 原則匯入邏輯會將原則運算式的規模限制在 4096 個節點來保護應用程式免於受到循環原則參考，當中的節點為下列其中一個項目：`wsp:Policy`、`wsp:All`、`wsp:ExactlyOne` 和 `wsp:policyReference`。  
  
 原則匯入邏輯同時會自動正規化原則運算式。 巢狀原則運算式和 `wsp:Optional` 屬性不會正規化。 所能完成的正規化處理數量將限制在 4096 個步驟，其中每個步驟都會產生原則判斷提示，或是 `wsp:ExactlyOne` 項目的子項目。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> 型別最多會嘗試 32 種附加至不同 WSDL 原則主體的各種原則替代方案組合。 如果沒有組合可以正常匯入，就會使用第一個組合來建構部分自訂繫結。  
  
## <a name="error-handling"></a>錯誤處理  
 <xref:System.ServiceModel.Description.MetadataExporter> 和 <xref:System.ServiceModel.Description.MetadataImporter> 型別都會公開 `Errors` 屬性，此屬性會分別包含匯出或匯入處理期間所遭遇的錯誤與警告訊息集合，以便在實作工具時使用。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> 型別一般會針對匯入處理期間所攔截的例外狀況擲回例外狀況，並將對應的錯誤新增至其 `Errors` 屬性中。 但是，<xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>、<xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> 和 <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> 方法並不會擲回這些例外狀況，因此您必須檢查 `Errors` 屬性，判斷在呼叫這些方法時是否發生任何問題。  
  
 <xref:System.ServiceModel.Description.WsdlExporter> 型別會在匯出處理期間重新擲回所有攔截到的例外狀況。 這些例外狀況不會在 `Errors` 屬性中當成錯誤來擷取。 一旦 <xref:System.ServiceModel.Description.WsdlExporter> 擲回例外狀況，就會呈現錯誤狀態而無法重複使用。 當因為使用萬用字元動作而無法匯出作業，以及當碰到重複的繫結名稱時，<xref:System.ServiceModel.Description.WsdlExporter> 就會將警告新增至自身的 `Errors` 屬性中。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：將中繼資料匯入服務端點](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 說明如何將下載的中繼資料匯入描述物件中。  
  
 [如何：從服務端點匯出中繼資料](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 說明如何將描述物件匯出至中繼資料。  
  
 [ServiceDescription 與 WSDL 參考](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 說明描述物件與 WSDL 之間的對應。  
  
 [如何：使用 Svcutil 從已編譯的服務程式代碼匯出中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 說明使用 Svcutil.exe 來匯出編譯組件中有關服務、合約與資料型別的中繼資料。  
  
 [資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 說明 <xref:System.Runtime.Serialization.DataContractSerializer> 用來描述 XML 序列化之 Common Language Runtime (CLR) 型別的 XML 結構描述 (XSD) 子集。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>另請參閱

- [匯出 WCF 延伸模組的自訂中繼資料](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [匯入 WCF 延伸模組的自訂中繼資料](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
