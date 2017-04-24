---
title: "指定端點位址 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "端點 [WCF] 定址"
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
caps.latest.revision: 41
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 41
---
# 指定端點位址
所有 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務的通訊都會透過其端點進行。 每個<xref:System.ServiceModel.Description.ServiceEndpoint>包含<xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>、<xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>，和<xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>。 合約會指定哪些為可用的作業。 繫結會指定如何與服務通訊，而位址則指定何處可找到服務。 每個端點必須具備唯一的位址。 端點位址由<xref:System.ServiceModel.EndpointAddress>類別，其中包含統一資源識別元 (URI)，表示服務的位址，<xref:System.ServiceModel.EndpointAddress.Identity%2A>，用來表示服務的安全性識別和選用的集合<xref:System.ServiceModel.EndpointAddress.Headers%2A>。 選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。 例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。  
  
## <a name="definition-of-an-endpoint-address"></a>端點位址的定義  
 在[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]、 <xref:System.ServiceModel.EndpointAddress>端點參考 (EPR) 的 Ws-addressing 標準中定義的模型。  
  
 大部分傳輸的位址 URI 具有四個部分。 例如，"http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" 這個 URI 便具有下列四個部分：  
  
-   配置：http:  
  
-   電腦：www.fabrikam.com  
  
-   (選擇性) 連接埠：322  
  
-   路徑：/mathservice.svc/secureEndpoint  
  
 EPR 模型的一部分，就是每個端點參考都包含可新增額外識別資訊的某些參考參數。 在[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，這些參考參數會模型化為的執行個體<xref:System.ServiceModel.Channels.AddressHeader>類別。  
  
 您可以強制使用程式碼，或是透過組態以宣告的形式來指定服務的端點位址。 在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。 一般來說，透過組態來定義服務端點會比透過程式碼來得實際一些。 將繫結和位址資訊留在程式碼外面可讓它們直接進行變更，而不需要重新編譯或重新部署應用程式。 如果在程式碼或組態中沒有指定端點，則執行階段會針對服務所實作的每個合約，在每個基底位址上加入一個預設端點。  
  
 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中，有兩種方式可以用來指定服務的端點位址。 您可以指定與服務相關聯的每個端點的絕對位址，或者您可以提供的基底位址<xref:System.ServiceModel.ServiceHost>的服務，然後指定相對於此基底位址會定義此服務相關聯的每個端點的位址。 您可以透過組態或程式碼，使用這些程序中的任何一個來指定服務的端點位址。 如果您沒有指定相對位址，則服務會使用基底位址。 您可以讓同一個服務使用多個基底位址，但是每個服務只允許每個傳輸使用一個基底位址。 如果您具有多個端點，而其中每一個都設定為不同的繫結，則其位址必須是唯一的。 使用相同繫結但不同合約的端點可以使用相同的位址。  
  
 使用 IIS 裝載時，您就不是管理<xref:System.ServiceModel.ServiceHost>自行執行個體。 裝載於 IIS 時，基底位址一律是服務的 .svc 檔案中指定的位址。 因此請務必針對 IIS 裝載的服務端點使用相對端點位址。 在部署服務時，提供完整的端點位址可能會導致錯誤。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][部署網際網路資訊服務裝載的 WCF 服務](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)。  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>在組態中定義端點位址  
 若要在組態檔中定義的端點，使用[ <> \> ](http://msdn.microsoft.com/zh-tw/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目。  
  
 <!-- TODO: review snippet reference [!code[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  -->  
  
 當<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>呼叫方法時 （亦即，當裝載應用程式會嘗試啟動服務），系統會尋找[ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/service.md)項目名稱屬性來指定 「 UE。Samples.HelloService 」。 如果[ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/service.md)找到項目，系統會載入指定的類別，並建立使用組態檔中提供的端點定義的端點。 這項機制可讓您透過兩行程式碼輕鬆地載入並啟動服務，同時不用在程式碼中留下繫結與位址資訊。 使用這種方法的好處是，您不用重新編譯或重新部署應用程式，便可進行這些變更。  
  
 選擇性標頭中宣告[ <> \</> \> ](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)。 下列是用來指定組態檔中服務端點的項目範例，此指定組態檔會區分以下兩個標頭的不同：來自 http://tempuri1.org/ 的 "Gold" 用戶端和來自 http://tempuri2.org/ 的 "Standard" 用戶端。 呼叫此服務的用戶端必須有適當[ <> \> ](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)其組態檔中。  
  
 <!-- TODO: review snippet reference [!code[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  -->  
  
 如先前所示，您也可以在個別訊息上設定標頭，而不是在某個端點的所有訊息上設定標頭。 這由使用<xref:System.ServiceModel.OperationContextScope>若要將自訂標頭新增至傳出的訊息，用戶端應用程式中建立新的內容，如下列範例所示。  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>中繼資料中的端點位址  
 在 Web 服務描述語言 (WSDL) 中，端點位址會表示為對應端點的 `EndpointReference` 項目中之 WS-Addressing `wsdl:port` (EPR) 項目。 EPR 包含端點的位址以及任何位址屬性。 請注意，`wsdl:port` 內的 EPR 會取代 `soap:Address`，如下列範例所示。  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>在程式碼中定義端點位址  
 可以建立的程式碼中的端點位址<xref:System.ServiceModel.EndpointAddress>類別。 您可以為端點位址指定完整路徑的 URI，或是相對於服務基底位址的路徑 URI。 下列程式碼說明如何建立的執行個體<xref:System.ServiceModel.EndpointAddress>類別，並將它加入至<xref:System.ServiceModel.ServiceHost>裝載服務的執行個體。  
  
 下列範例示範如何在程式碼中指定完整端點位址。  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 下列範例示範如何將相對位址 ("MyService") 新增至服務主機的基底位址。  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  屬性的<xref:System.ServiceModel.Description.ServiceDescription>服務中的應用程式絕不能修改之後<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A>方法<xref:System.ServiceModel.ServiceHostBase>。 一些成員，例如<xref:System.ServiceModel.ServiceHostBase.Credentials%2A>屬性和`AddServiceEndpoint`方法<xref:System.ServiceModel.ServiceHostBase>和<xref:System.ServiceModel.ServiceHost>，如果通過該點之後修改，會擲回例外狀況。 其他成員可讓您加以修改，但結果仍未定義。  
>   
>  同樣地，在用戶端<xref:System.ServiceModel.Description.ServiceEndpoint>值不會修改呼叫之後<xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A>上<xref:System.ServiceModel.ChannelFactory>。 <xref:System.ServiceModel.ChannelFactory.Credentials%2A>屬性在該點之後修改，會擲回例外狀況。 其他的用戶端說明值可以修改而不會造成錯誤，但是結果仍為未定義。  
>   
>  是否在服務或用戶端，建議您修改的描述，然後才呼叫<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>。  
  
## <a name="using-default-endpoints"></a>使用預設端點  
 如果在程式碼或組態中沒有指定端點，則執行階段會針對服務所實作的每個服務合約，在每個基底位址上加入一個預設端點，藉以提供預設端點。 您可以指定基底的位址，在程式碼，或在組態中，並會加入預設端點時<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>上稱為<xref:System.ServiceModel.ServiceHost>。  
  
 如果沒有明確提供端點的預設端點仍加入藉由呼叫<xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A>上<xref:System.ServiceModel.ServiceHost>之前，先呼叫<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]預設端點、 繫結和行為，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.EndpointAddress>   
 [服務身分識別與驗證](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [裝載](../../../docs/framework/wcf/feature-details/hosting.md)