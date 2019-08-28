---
title: 指定端點位址
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 6f62d0f712f7461ef8cd65f15f3ed2690446bae1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044461"
---
# <a name="specifying-an-endpoint-address"></a>指定端點位址

所有與 Windows Communication Foundation (WCF) 服務的通訊都是透過其端點進行。 每個 <xref:System.ServiceModel.Description.ServiceEndpoint> 都包含有 <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>、<xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A> 和 <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>。 合約會指定哪些為可用的作業。 繫結會指定如何與服務通訊，而位址則指定何處可找到服務。 每個端點必須具備唯一的位址。 端點位址是由 <xref:System.ServiceModel.EndpointAddress> 類別所代表，其中包含代表服務位址的統一資源識別元 (URI)、代表服務之安全性身分識別的 <xref:System.ServiceModel.EndpointAddress.Identity%2A>，以及選用的 <xref:System.ServiceModel.EndpointAddress.Headers%2A> 集合。 選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。 例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。

## <a name="definition-of-an-endpoint-address"></a>端點位址的定義

在 WCF 中, <xref:System.ServiceModel.EndpointAddress>會依照 ws-addressing 標準中的定義, 將端點參考 (EPR) 模型在一起。

大部分傳輸的位址 URI 具有四個部分。 例如, 此 URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint`有下列四個部分:

- 配置：http:

- 機器碼`www.fabrikam.com`

- 選擇性移植322

- 路徑：/mathservice.svc/secureEndpoint

EPR 模型的一部分，就是每個端點參考都包含可新增額外識別資訊的某些參考參數。 在 WCF 中, 這些參考參數會模型化為<xref:System.ServiceModel.Channels.AddressHeader>類別的實例。

您可以強制使用程式碼，或是透過組態以宣告的形式來指定服務的端點位址。 在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。 一般來說，透過組態來定義服務端點會比透過程式碼來得實際一些。 將繫結和位址資訊留在程式碼外面可讓它們直接進行變更，而不需要重新編譯或重新部署應用程式。 如果在程式碼或組態中沒有指定端點，則執行階段會針對服務所實作的每個合約，在每個基底位址上加入一個預設端點。

有兩種方式可以指定 WCF 中服務的端點位址。 您可以為每個與服務相關聯的端點指定絕對位址，或是為服務的 <xref:System.ServiceModel.ServiceHost> 提供基底位址，然後指定相對於此基底位址所定義之服務相關聯的每個端點位址。 您可以透過組態或程式碼，使用這些程序中的任何一個來指定服務的端點位址。 如果您沒有指定相對位址，則服務會使用基底位址。 您可以讓同一個服務使用多個基底位址，但是每個服務只允許每個傳輸使用一個基底位址。 如果您具有多個端點，而其中每一個都設定為不同的繫結，則其位址必須是唯一的。 使用相同繫結但不同合約的端點可以使用相同的位址。

使用 IIS 裝載時，您不用自行管理 <xref:System.ServiceModel.ServiceHost> 執行個體。 裝載於 IIS 時，基底位址一律是服務的 .svc 檔案中指定的位址。 因此請務必針對 IIS 裝載的服務端點使用相對端點位址。 在部署服務時，提供完整的端點位址可能會導致錯誤。 如需詳細資訊, 請參閱[部署 Internet Information Services 託管的 WCF 服務](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)。

## <a name="defining-endpoint-addresses-in-configuration"></a>在組態中定義端點位址

若要在設定檔中定義端點, 請使用[ \<端點 >](../configure-apps/file-schema/wcf/endpoint-element.md)元素。

[!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]

呼叫方法時 (也就是當裝載應用程式嘗試啟動服務時), 系統會尋找[ \<](../../../docs/framework/configure-apps/file-schema/wcf/service.md)具有指定 "UE" 之 name 屬性的服務 > 元素。 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>範例. HelloService」。 如果找到服務 > 元素, 系統就會載入指定的類別, 並使用設定檔中提供的端點定義來建立端點。 [ \< ](../../../docs/framework/configure-apps/file-schema/wcf/service.md) 這項機制可讓您透過兩行程式碼輕鬆地載入並啟動服務，同時不用在程式碼中留下繫結與位址資訊。 使用這種方法的好處是，您不用重新編譯或重新部署應用程式，便可進行這些變更。

選擇性標頭會在 > 的[ \<標頭](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)中宣告。 以下是在設定檔中用來為服務指定端點的元素範例, 可區別兩個標頭:來自的「金級`http://tempuri1.org/` 」用戶端和來自`http://tempuri2.org/`的「標準」用戶端。 呼叫此服務的用戶端必須在其設定檔中[ \<> 適當的標頭](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)。

[!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]

如先前所示，您也可以在個別訊息上設定標頭，而不是在某個端點的所有訊息上設定標頭。 如下列範例所示，您可以使用 <xref:System.ServiceModel.OperationContextScope> 在用戶端應用程式上建立新的內容，將自訂標頭新增至傳出的訊息，以完成這項工作。

[!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
[!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]

## <a name="endpoint-address-in-metadata"></a>中繼資料中的端點位址

在 Web 服務描述語言 (WSDL) 中，端點位址會表示為對應端點的 `EndpointReference` 項目中之 WS-Addressing `wsdl:port` (EPR) 項目。 EPR 包含端點的位址以及任何位址屬性。 請注意，`wsdl:port` 內的 EPR 會取代 `soap:Address`，如下列範例所示。

## <a name="defining-endpoint-addresses-in-code"></a>在程式碼中定義端點位址

您可以使用 <xref:System.ServiceModel.EndpointAddress> 類別，在程式碼中建立端點位址。 您可以為端點位址指定完整路徑的 URI，或是相對於服務基底位址的路徑 URI。 下列程式碼說明如何建立 <xref:System.ServiceModel.EndpointAddress> 類別的執行個體，並將其新增至裝載服務的 <xref:System.ServiceModel.ServiceHost> 執行個體。

下列範例示範如何在程式碼中指定完整端點位址。

[!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]

下列範例示範如何將相對位址 ("MyService") 新增至服務主機的基底位址。

[!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]

> [!NOTE]
> 在服務應用程式中 <xref:System.ServiceModel.Description.ServiceDescription> 的屬性，絕對不能在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 上的 <xref:System.ServiceModel.ServiceHostBase> 方法之後遭到修改。 如果在通過該點之後修改一些成員，像是 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性及 `AddServiceEndpoint` 與 <xref:System.ServiceModel.ServiceHostBase> 上的 <xref:System.ServiceModel.ServiceHost> 方法，便會擲回例外狀況。 其他成員可讓您加以修改，但結果仍未定義。
>
> 同樣地，您不可以在呼叫 <xref:System.ServiceModel.Description.ServiceEndpoint> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之後修改用戶端上的 <xref:System.ServiceModel.ChannelFactory> 值。 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 屬性如果在通過該點之後修改，便會擲回例外狀況。 其他的用戶端說明值可以修改而不會造成錯誤，但是結果仍為未定義。
>
> 無論是在服務或是用戶端，建議的做法都是在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前修改說明。

## <a name="using-default-endpoints"></a>使用預設端點

如果在程式碼或組態中沒有指定端點，則執行階段會針對服務所實作的每個服務合約，在每個基底位址上加入一個預設端點，藉以提供預設端點。 基底位址可以在程式碼或組態中指定，而預設端點則會在 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 上呼叫 <xref:System.ServiceModel.ServiceHost> 時加入。

如果沒有明確提供端點，在呼叫 <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> 之前，仍可藉由在 <xref:System.ServiceModel.ServiceHost> 上呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 來加入預設端點。 如需預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.EndpointAddress>
- [服務身分識別和驗證](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [建立端點概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [裝載](../../../docs/framework/wcf/feature-details/hosting.md)
