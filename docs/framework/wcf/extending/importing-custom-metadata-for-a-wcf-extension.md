---
title: "匯入 WCF 擴充的自訂中繼資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 匯入 WCF 擴充的自訂中繼資料
在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中，中繼資料匯入指的是從中繼資料中產生服務的抽象表示法或其元件部分的處理序。例如，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以從 WSDL 文件中為服務匯入 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體、<xref:System.ServiceModel.Channels.Binding> 執行個體或 <xref:System.ServiceModel.Description.ContractDescription> 執行個體。若要將服務中繼資料匯入 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請使用 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 抽象類別的實作。衍生自 <xref:System.ServiceModel.Description.MetadataImporter> 類別實作的類型，會支援匯入中繼資料格式以利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 WS\-Policy 匯入邏輯。  
  
 自訂中繼資料包含系統提供的中繼資料匯入工具無法匯入的 XML 項目。一般來說，包含自訂 WSDL 延伸與自訂原則判斷提示。  
  
 本節說明如何匯入自訂 WSDL 延伸與原則判斷提示，但不強調如何匯入處理序。如需如何使用可匯出與匯入中繼資料 \(不管該中繼資料為自訂或系統所支援的\) 類型的詳細資訊，請參閱[匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)。  
  
## 概觀  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 類型是包含在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 <xref:System.ServiceModel.Description.MetadataImporter> 抽象類別的實作。<xref:System.ServiceModel.Description.WsdlImporter> 類型會匯入具有與 <xref:System.ServiceModel.Description.MetadataSet?displayProperty=fullName> 物件組合在一起之附加原則的 WSDL 中繼資料。預設之匯入工具無法辨識的原則判斷提示與 WSDL 延伸會傳遞至任何已註冊的自訂原則與 WSDL 匯入工具以便匯入。一般來說，匯入工具經過實作後，可支援使用者定義的繫結項目或是可修改匯入的合約。  
  
 本章節內容：  
  
1.  如何實作並使用 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName> 介面，以便在產生描述與程式碼之前將 WSDL 資料公開至自訂匯入工具。您可以透過此介面來檢查或修改使用特定中繼資料集合來執行的描述類型與程式碼編譯。  
  
2.  如何實作並使用 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> 介面，以便在產生描述物件之前將原則判斷提示公開到匯入工具。您可以使用此介面來檢查或修改以下載原則為基礎的繫結或合約。  
  
 如需匯出自訂 WSDL 與原則判斷提示的詳細資訊，請參閱[匯出 WCF 擴充的自訂中繼資料](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)。  
  
## 匯入自訂 WSDL 延伸  
 若要新增對匯入 WSDL 延伸的支援，請實作 <xref:System.ServiceModel.Description.IWsdlImportExtension> 介面，然後將您的實作新增至 <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> 屬性。<xref:System.ServiceModel.Description.WsdlImporter> 也可以將 <xref:System.ServiceModel.Description.IWsdlImportExtension> 介面 \(在您的應用程式組態檔中註冊\) 的實作載入。請注意，預設會註冊一些 WSDL 匯入工具，而且註冊之 WSDL 匯入工具的順序很重要。  
  
 一旦 <xref:System.ServiceModel.Description.WsdlImporter> 載入並使用自訂 WSDL 匯入工具，在匯入處理序開始之前會先呼叫 <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> 方法來啟用中繼資料的修改作業。接下來，會匯入合約並呼叫 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> 方法來啟用由中繼資料匯入之合約的修改作業。最後，呼叫 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> 方法來啟用匯入端點的修改作業。  
  
 如需詳細資訊，請參閱 [HOW TO：匯入自訂 WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)。  
  
### 匯入自訂原則判斷提示  
 <xref:System.ServiceModel.Description.WsdlImporter> 類型與 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 會自動處理附加至 WSDL 文件的原則運算式中，各種不同的原則判斷提示類型。這些工具會負責收集、正常化與合併附加至 WSDL 繫結與 WSDL 連接埠的原則運算式。  
  
 若要新增對匯入自訂原則判斷提示的支援，請實作 <xref:System.ServiceModel.Description.IPolicyImportExtension> 介面，然後將您的實作新增至 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> 屬性。<xref:System.ServiceModel.Description.MetadataImporter> 也可以將 <xref:System.ServiceModel.Description.IPolicyImportExtension> 介面 \(在您的應用程式組態檔中註冊\) 的實作載入。請注意，預設會註冊一些原則匯入工具，而且註冊之原則匯入工具的順序很重要。  
  
 中繼資料系統會針對附加至訊息、作業與端點原則主體的每個原則替代項目組合，在所有已註冊的原則匯入延伸上重複呼叫 <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName> 方法。一旦匯入 WSDL 連接埠，附加至連接埠與對應 WSDL 繫結的原則會在呼叫原則匯入延伸之前合併。原則替代項目會透過 <xref:System.ServiceModel.Description.PolicyConversionContext> 以 <xref:System.ServiceModel.Description.PolicyAssertionCollection> 物件形式來提供。每一個 <xref:System.ServiceModel.Description.PolicyAssertionCollection> 都是由 <xref:System.Xml.XmlElement> 物件所表示的原則判斷提示集合。  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext> 物件上的 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> 和 <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> 屬性都會公開從 WSDL 所匯入的 <xref:System.ServiceModel.Description.ContractDescription> 和 <xref:System.ServiceModel.Channels.BindingElement> 物件。原則匯入延伸會透過下列方式處理原則判斷提示：尋找特定原則判斷提示類型的執行個體、對 <xref:System.ServiceModel.Description.ContractDescription> 或 <xref:System.ServiceModel.Channels.BindingElement> 物件執行對應的變更，然後再從對應的 <xref:System.ServiceModel.Description.PolicyAssertionCollection> 執行個體移除原則判斷提示。  
  
 `wsp:Optional` 屬性與巢狀原則運算式尚未正常化，因此原則匯入延伸必須處理這些原則建構。同時，您也可以使用相同的 <xref:System.ServiceModel.Description.ContractDescription> 和 <xref:System.ServiceModel.Channels.BindingElement> 物件來多次呼叫原則匯入延伸，證明了原則匯入延伸應該禁得起此行為的重複使用。  
  
> [!IMPORTANT]
>  無效或不適當的中繼資料可以傳遞至匯入工具。請確定自訂匯入工具禁得起所有格式的 XML 使用。  
  
## 請參閱  
 [HOW TO：匯入自訂 WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)   
 [HOW TO：匯入自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)   
 [HOW TO：撰寫 ServiceContractGenerator 的擴充](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)