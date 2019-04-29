---
title: 用戶端架構
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 4ced24f370e2ab54528c6adb2b3617d3d849e745
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781520"
---
# <a name="client-architecture"></a>用戶端架構
應用程式會使用 Windows Communication Foundation (WCF) 用戶端物件來叫用服務作業。 本主題討論 WCF 用戶端物件、 WCF 用戶端通道，以及基礎通道架構及其關聯性。 WCF 用戶端物件的基本概觀，請參閱 < [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)。 如需通道層的詳細資訊，請參閱[擴充通道層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## <a name="overview"></a>總覽  
 服務模型執行階段會建立 WCF 用戶端，是由下列所組成：  
  
- 自動產生的服務合約用戶端實作，它會將您應用程式程式碼的呼叫轉變為傳出訊息，並將回應訊息轉變為輸出參數，然後傳回您應用程式可以擷取的值。  
  
- 控制項介面的實作 (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>)，它會將各種介面分組並提供存取控制功能，尤其是關閉用戶端工作階段並處置通道的能力。  
  
- 用戶端通道，它是採用已使用繫結所指定的組態設定為建構基礎。  
  
 應用程式可以依需求，透過建立這類用戶端<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>或建立的執行個體<xref:System.ServiceModel.ClientBase%601>衍生類別，它會產生[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 這些已建置的用戶端類別會封裝及委派 (Delegate) 至 <xref:System.ServiceModel.ChannelFactory> 所動態建構的用戶端通道實作。 因此，用戶端通道以及產生通道的通道處理站將是本項討論內容的重點。  
  
## <a name="client-objects-and-client-channels"></a>用戶端物件和用戶端通道  
 WCF 用戶端的基底介面就<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>介面，以便公開用戶端的核心功能，以及基本的通訊物件功能<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>的內容功能<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>，以及可延伸的行為<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 不過，<xref:System.ServiceModel.IClientChannel> 介面本身並不會定義服務合約。 這些由服務合約介面宣告 (通常是從服務中繼資料使用之類的工具產生[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md))。 WCF 用戶端型別會擴充<xref:System.ServiceModel.IClientChannel>和目標的服務合約介面，可讓應用程式直接呼叫作業並且也可以存取用戶端執行階段功能。 建立 WCF 用戶端提供 WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>建立執行的階段所需的資訊，可連接並與設定的服務端點互動的物件。  
  
 如先前所述，您才能使用它們必須設定兩個 WCF 用戶端類型。 最簡單的 WCF 用戶端類型是衍生自<xref:System.ServiceModel.ClientBase%601>(或<xref:System.ServiceModel.DuplexClientBase%601>如果服務合約是雙工合約)。 您可以使用以程式設計方式所設定的建構函式 (Constructor) 或使用組態檔來建立這些類型，接著就可以直接呼叫這些類型來叫用服務作業。 如需的基本概觀<xref:System.ServiceModel.ClientBase%601>物件，請參閱[WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)。  
  
 第二種類型則是在從呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> 方法的執行階段期間所產生。 通常涉及嚴格控制通訊特性的應用程式會使用此用戶端類型，稱為*用戶端通道物件*，因為它可讓更為直接的互動比基礎用戶端執行階段和通道系統。  
  
## <a name="channel-factories"></a>通道處理站  
 負責建立可支援用戶端引動過程之基礎執行階段的類別為 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 類別。 WCF 用戶端物件和 WCF 用戶端通道物件則使用<xref:System.ServiceModel.ChannelFactory%601>物件來建立執行個體;<xref:System.ServiceModel.ClientBase%601>衍生的用戶端物件會封裝通道處理站的處理，但是許多案例對於合理使用通道處理站直接。 例如當您想要重複地從現有的處理站建立新的用戶端通道，就是這種情形的常見案例。 如果您使用的用戶端物件，您可以藉由呼叫從 WCF 用戶端物件取得基礎通道處理站<xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType>屬性。  
  
 對於通道處理站，請特別記住它們會先針對提供給它們的組態建立用戶端通道的新執行個體，然後才呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。 一旦您呼叫<xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>(或<xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>， <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>，或在 WCF 用戶端物件上的任何作業)，您無法修改通道處理站，並預期以取得不同的服務執行個體的通道，即使您只想要變更目標端點位址。 如果想要使用不同的組態來建立用戶端物件或用戶端通道，您就必須先建立新的通道處理站。  
  
 如需有關使用 WCF 用戶端物件和 WCF 用戶端通道的各種問題的詳細資訊，請參閱[使用 WCF 用戶端存取服務](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。  
  
 下列兩節會說明建立和使用的 WCF 用戶端通道物件。  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>建立新的 WCF 用戶端通道物件  
 為了說明用戶端通道的使用方式，請假設已產生下列服務合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 若要連接至 `ISampleService` 服務，請直接搭配通道處理站 (<xref:System.ServiceModel.ChannelFactory%601>) 使用產生的合約介面。 在建立並設定特定之合約的通道處理站之後，您就可以呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> 方法，傳回可以用來與 `ISampleService` 服務進行通訊的用戶端通道物件。  
  
 當使用含有服務合約介面的 <xref:System.ServiceModel.ChannelFactory%601> 類別時，您必須轉換為 <xref:System.ServiceModel.IClientChannel> 介面，以明確開啟、關閉或中止通道。 為了讓這個類別更容易使用，Svcutil.exe 工具會另外產生可以實作服務合約介面和 <xref:System.ServiceModel.IClientChannel> 兩者的協助程式介面，讓您可以不用轉型就與用戶端通道基礎結構進行互動。 下列程式碼會示範實作前述服務合約之協助程式用戶端通道的定義。  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>建立新的 WCF 用戶端通道物件  
 若要使用用戶端通道連接至 `ISampleService` 服務，請傳遞合約介面類型做為型別參數，直接搭配通道處理站使用產生的合約介面 (或是協助程式版本)。 在已建立並設定特定之合約的通道處理站之後，您就可以呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> 方法，傳回可以用來與 `ISampleService` 服務進行互動的用戶端通道物件。  
  
 建立之後，用戶端通道物件就會實作 <xref:System.ServiceModel.IClientChannel> 和合約介面。 因此，您就可以直接使用它們，呼叫與支援該合約之服務進行互動的作業。  
  
 使用用戶端物件和使用用戶端通道物件之間的差別，端視哪種方式對於開發人員而言屬於方便控制和容易使用。 許多開發人員會習慣使用類別和物件會偏好使用 WCF 用戶端物件，而不是 WCF 用戶端通道。  
  
 如需範例，請參閱[如何：使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)。
