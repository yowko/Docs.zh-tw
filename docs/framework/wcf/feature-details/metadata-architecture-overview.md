---
title: "中繼資料架構概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中繼資料 [WCF], 概觀"
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# 中繼資料架構概觀
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供豐富的基礎結構，讓您匯出、發行、擷取與匯入服務中繼資料。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務使用中繼資料說明如何與服務端點互動，讓 Svcutil.exe 之類的工具可以自動產生用戶端程式碼來存取服務。  
  
 組成 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中繼資料基礎結構的大部分型別都駐留在 <xref:System.ServiceModel.Description> 命名空間中。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 <xref:System.ServiceModel.Description.ServiceEndpoint> 類別來說明服務中的端點。您可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來產生服務端點的中繼資料，或是匯入服務中繼資料來產生 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將服務的中繼資料表示為 <xref:System.ServiceModel.Description.MetadataSet> 型別的執行個體，而其所屬結構將與 WS\-MetadataExchange 中定義的中繼資料序列化格式緊密結合。<xref:System.ServiceModel.Description.MetadataSet> 型別會與實際的服務中繼資料包裹在一起，例如 Web 服務描述語言 \(WSDL\) 文件、XML 結構描述文件，或是 WS\-Policy 運算式，做為 <xref:System.ServiceModel.Description.MetadataSection> 執行個體集合。每個 <xref:System.ServiceModel.Description.MetadataSection?displayProperty=fullName> 執行個體都包含特定的中繼資料方言與一個識別元。<xref:System.ServiceModel.Description.MetadataSection?displayProperty=fullName> 可能在其 <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=fullName> 屬性中包含下列項目：  
  
-   原始中繼資料。  
  
-   <xref:System.ServiceModel.Description.MetadataReference> 執行個體。  
  
-   <xref:System.ServiceModel.Description.MetadataLocation> 執行個體。  
  
 <xref:System.ServiceModel.Description.MetadataReference?displayProperty=fullName> 執行個體會指向另一個中繼資料交換 \(MEX\) 端點，而 <xref:System.ServiceModel.Description.MetadataLocation?displayProperty=fullName> 執行個體則是透過 HTTP URL 指向中繼資料文件。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援使用 WSDL 文件來描述服務端點、服務合約、繫結、訊息交換模式、訊息與服務所實作的錯誤訊息。服務所使用的資料型別會透過 XML 結構描述於 WSDL 文件中說明。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][結構描述匯入和匯出](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md).您可以針對服務行為、合約行為，以及延伸服務功能的繫結項目，使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來匯出與匯入 WSDL 延伸。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][匯出 WCF 擴充的自訂中繼資料](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## 匯出服務中繼資料  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，「*中繼資料匯出*」\(Metadata Export\) 這項程序會描述服務端點並將其投射至並行標準化表示法，以供用戶端用來了解如何使用服務。若要從 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體匯出中繼資料，請使用 <xref:System.ServiceModel.Description.MetadataExporter> 抽象類別的實作。<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 實作會產生可封裝到 <xref:System.ServiceModel.Description.MetadataSet> 執行個體的中繼資料。  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 類別所提供的架構可產生原則運算式，用來說明端點繫結及其相關作業、訊息，與錯誤的各項功能與需求。這些原則運算式是在 <xref:System.ServiceModel.Description.PolicyConversionContext> 執行個體中擷取。<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 實作可接著將這些原則運算式附加到所產生的中繼資料中。  
  
 在產生 <xref:System.ServiceModel.Description.PolicyConversionContext> 物件以供 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 實作使用時，<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 會呼叫每個可於 <xref:System.ServiceModel.Description.ServiceEndpoint> 繫結中實作 <xref:System.ServiceModel.Description.IPolicyExportExtension> 介面的 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName>。您可以在自訂的 <xref:System.ServiceModel.Channels.BindingElement> 型別實作中實作 <xref:System.ServiceModel.Description.IPolicyExportExtension> 介面，以匯出新原則判斷提示。  
  
 <xref:System.ServiceModel.Description.WsdlExporter> 型別是包含在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> 抽象類別的實作。<xref:System.ServiceModel.Description.WsdlExporter> 型別會產生包含附加原則運算式的 WSDL 中繼資料。  
  
 若要針對端點行為、合約行為，或服務端點中的繫結項目匯出自訂 WSDL 中繼資料或 WSDL 延伸，可以實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 介面。產生 WSDL 文件時，<xref:System.ServiceModel.Description.WsdlExporter> 會尋找 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體，看看是否有可實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 介面的繫結項目、作業行為、合約行為，以及端點行為。  
  
## 發行服務中繼資料  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會藉由公開一個或多個中繼資料端點以發行中繼資料。發行服務中繼資料會使用標準化的通訊協定 \(例如 MEX 和 HTTP\/GET 要求\) 來提供服務中繼資料。中繼資料端點與其他服務端點相似的地方，在於都有位址、繫結和合約。您可以透過組態或程式碼，將中繼資料端點新增至服務主機。  
  
 若要發行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的中繼資料端點，您必須先將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為的執行個體新增至服務。將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 執行個體新增至服務，會藉由公開一個或多個中繼資料端點來提升服務發行中繼資料的能力。一旦您新增了 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 服務行為之後，就可以接著公開支援 MEX 通訊協定的中繼資料端點，或公開回應 HTTP\/GET 要求的中繼資料端點。  
  
 若要新增使用 MEX 通訊協定的中繼資料端點，請將服務端點新增至使用名為 IMetadataExchange 服務合約的服務主機。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會定義具有此服務合約名稱的 <xref:System.ServiceModel.Description.IMetadataExchange> 介面。WS\-MetadataExchange 端點或 MEX 端點都可以使用靜態處理站方法在 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別上所公開的四個預設繫結中的其中一個，以比對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工具 \(例如 Svcutil.exe\) 使用的預設繫結。您也可以使用自訂繫結設定 MEX 中繼資料端點。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 會使用 <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=fullName> 匯出服務中所有服務端點的中繼資料。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]從服務匯出中繼資料的詳細資訊，請參閱[匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 會將 <xref:System.ServiceModel.Description.ServiceMetadataExtension> 執行個體新增為服務主機的延伸以提升您的服務主機效能。<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> 為中繼資料發行通訊協定提供實作。您也可以藉由存取 <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> 屬性，使用 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> 在執行階段取得服務的中繼資料。  
  
> [!CAUTION]
>  如果您在應用程式組態檔中加入 MEX 端點，然後嘗試從程式碼將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 加入至服務主機，則會收到下列例外狀況：  
>   
>  System.InvalidOperationException: 在服務 Service1 實作的合約清單中，找不到合約名稱 'IMetadataExchange'。請直接將 ServiceMetadataBehavior 新增至組態檔或 ServiceHost，直接啟用此合約的支援。  
>   
>  若要解決此問題，您可以在組態檔中加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>，或是從程式碼一併加入該端點及 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>。  
>   
>  如需在應用程式組態檔中加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 的範例，請參閱[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。如需從程式碼加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 的範例，請參閱[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)範例。  
  
> [!CAUTION]
>  如果某服務公開兩份不同的服務合約，而這些合約包含了同名的作業，發行該服務的中繼資料時會擲回例外狀況。例如，假設某服務既公開具有 Get\(Car c\) 作業且名為 ICarService 的服務合約，又公開具有 Get\(Book b\) 作業且名為 IBookService 的服務合約，則一旦產生該服務的中繼資料便會擲回例外狀況或顯示錯誤訊息。為了解決此問題，請執行下列其中一項：  
>   
>  -   重新命名其中一項作業。  
> -   將 <xref:System.ServiceModel.OperationContractAttribute.Name%2A> 設定為另一個名稱。  
> -   使用 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性，將其中一項作業的命名空間設定為另一個命名空間。  
  
## 擷取服務中繼資料  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以使用像是 WS\-MetadataExchange 和 HTTP 的標準化通訊協定來擷取服務中繼資料。這兩種通訊協定都由 <xref:System.ServiceModel.Description.MetadataExchangeClient> 型別所支援。您可以藉由提供位址及選擇性繫結，來擷取使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 型別的服務中繼資料。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 執行個體使用的繫結可以是以下預設繫結之一：<xref:System.ServiceModel.Description.MetadataExchangeBindings> 靜態類別、使用者提供的繫結，或是從 `IMetadataExchange` 合約的端點組態載入的繫結。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 也可以使用 <xref:System.Net.HttpWebRequest> 型別將 HTTP URL 參照解析為中繼資料。  
  
 根據預設，<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 執行個體與單一的 <xref:System.ServiceModel.Channels.ChannelFactoryBase> 執行個體有密切的關係。您可以透過覆寫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> 虛擬方法，以變更或取代 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 所使用的 <xref:System.ServiceModel.Channels.ChannelFactoryBase> 執行個體。同樣地，您可以覆寫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=fullName> 虛擬方法，以變更或取代由 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 使用的 <xref:System.Net.HttpWebRequest?displayProperty=fullName> 執行個體。  
  
 您可以使用 Svcutil.exe 工具並將 **\/target:metadata** 參數傳遞至某個位址，以使用 WS\-MetadataExchange 或 HTTP\/GET 要求來擷取服務中繼資料。Svcutil.exe 會在指定的位址下載中繼資料，並將檔案儲存到磁碟中。Svcutil.exe 會在內部使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 執行個體，而且會從應用程式組態檔載入 MEX 端點組態，而其名稱必須符合傳遞至 Svcutil.exe 的位址 \(如果存在的話\) 配置。否則，Svcutil.exe 預設會使用 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 靜態處理站型別所定義的其中一個繫結。  
  
## 匯入服務中繼資料  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，中繼資料匯入指的是從中繼資料中產生服務的抽象表示法或其元件部分的處理序。例如，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以從 WSDL 文件中為服務匯入 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體、<xref:System.ServiceModel.Channels.Binding> 執行個體或 <xref:System.ServiceModel.Description.ContractDescription> 執行個體。若要將服務中繼資料匯入 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請使用 <xref:System.ServiceModel.Description.MetadataImporter> 抽象類別的實作。衍生自 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 類別實作的型別，會支援匯入中繼資料格式以利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 WS\-Policy 匯入邏輯。  
  
 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 實作會收集附加至 <xref:System.ServiceModel.Description.PolicyConversionContext> 物件內服務中繼資料的原則運算式。<xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 接著會呼叫 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> 屬性中的 <xref:System.ServiceModel.Description.IPolicyImportExtension> 介面實作，將原則當成匯入中繼資料作業的一部分來處理。  
  
 您可以將自己的 <xref:System.ServiceModel.Description.IPolicyImportExtension> 介面實作新增至 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 執行個體上的 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> 集合，以便在將新原則判斷提示匯入 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 時提供更多支援。或者，您可以在自己的用戶端應用程式組態檔中註冊自己的原則匯入延伸。  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 型別是包含在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=fullName> 抽象類別的實作。<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 型別會匯入具有與 <xref:System.ServiceModel.Description.MetadataSet> 物件組合在一起之附加原則的 WSDL 中繼資料。  
  
 您可以實作 <xref:System.ServiceModel.Description.IWsdlImportExtension> 介面，然後將實作新增至 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 執行個體上的 <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> 屬性中，以便在匯入 WSDL 延伸時提供更多支援。<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 也可以將 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName> 介面 \(在您的用戶端應用程式組態檔中註冊\) 的實作載入。  
  
## 動態繫結  
 當端點繫結變更，或當您想要建立使用相同合約但具有不同繫結的端點通道時，可以針對用來建立服務端點通道的繫結進行動態更新。您可以針對可實作特定合約的服務端點使用 <xref:System.ServiceModel.Description.MetadataResolver> 靜態類別，於執行階段擷取並匯入中繼資料。您可以接著使用匯入的 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName> 物件來建立所需端點的用戶端或通道處理站。  
  
## 請參閱  
 <xref:System.ServiceModel.Description>   
 [中繼資料格式](../../../../docs/framework/wcf/feature-details/metadata-formats.md)   
 [匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)   
 [發行中繼資料](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)   
 [擷取中繼資料](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)   
 [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)   
 [中繼資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)   
 [擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)