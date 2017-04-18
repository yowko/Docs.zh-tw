---
title: "用戶端架構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 用戶端架構
應用程式會使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端物件來叫用服務作業。本主題將討論 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道，以及它們與基礎通道架構之間的關係。如需 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件的基本概觀，請參閱 [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]通道層的詳細資訊，請參閱[擴充通道層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## 概觀  
 服務模型執行階段會建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，該用戶端是由下列項目所組成：  
  
-   自動產生的服務合約用戶端實作，它會將您應用程式程式碼的呼叫轉變為傳出訊息，並將回應訊息轉變為輸出參數，然後傳回您應用程式可以擷取的值。  
  
-   控制項介面的實作 \(<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>\)，它會將各種介面分組並提供存取控制功能，尤其是關閉用戶端工作階段並處置通道的能力。  
  
-   用戶端通道，它是採用已使用繫結所指定的組態設定為建構基礎。  
  
 應用程式可以視需要建立此類用戶端，不論是透過 <xref:System.ServiceModel.ChannelFactory?displayProperty=fullName>，或是透過建立 <xref:System.ServiceModel.ClientBase%601> 衍生類別 \(由 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 所產生\) 的執行個體來進行建立。這些已建置的用戶端類別會封裝及委派 \(Delegate\) 至 <xref:System.ServiceModel.ChannelFactory> 所動態建構的用戶端通道實作。因此，用戶端通道以及產生通道的通道處理站將是本項討論內容的重點。  
  
## 用戶端物件和用戶端通道  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的基底介面為 <xref:System.ServiceModel.IClientChannel?displayProperty=fullName> 介面，它會公開 \(Expose\) 核心的用戶端功能以及 <xref:System.ServiceModel.ICommunicationObject?displayProperty=fullName> 的基礎通訊物件功能、<xref:System.ServiceModel.IContextChannel?displayProperty=fullName> 的內容功能和 <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=fullName> 的可延伸行為。  
  
 不過，<xref:System.ServiceModel.IClientChannel> 介面本身並不會定義服務合約。這些合約是由服務合約介面宣告 \(通常是使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)之類的工具從服務中繼資料所產生\)。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端型別會擴充 <xref:System.ServiceModel.IClientChannel> 和目標的服務合約介面，讓應用程式可以直接呼叫作業並且可以存取用戶端的執行階段功能。建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，可以為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> 物件提供當建立能夠與已設定服務端點進行連線和互動之執行階段時所需要的資訊。  
  
 如先前所述，這兩種 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類型必須先完成設定，才能供您使用。最簡單的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類型是衍生自 <xref:System.ServiceModel.ClientBase%601> \(如果服務合約為雙工合約，則為 <xref:System.ServiceModel.DuplexClientBase%601>\) 的物件。您可以使用以程式設計方式所設定的建構函式 \(Constructor\) 或使用組態檔來建立這些類型，接著就可以直接呼叫這些類型來叫用服務作業。如需 <xref:System.ServiceModel.ClientBase%601> 物件的基本概觀，請參閱 [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)。  
  
 第二種類型則是在從呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> 方法的執行階段期間所產生。考慮到嚴格控制通訊特性的應用程式，通常會使用這個稱為「*用戶端通道物件*」\(Client Channel Object\) 的類型，因為它可以提供比基礎用戶端執行階段和通道系統更為直接的互動。  
  
## 通道處理站  
 負責建立可支援用戶端引動過程之基礎執行階段的類別為 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName> 類別。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道物件兩者都會使用 <xref:System.ServiceModel.ChannelFactory%601> 物件來建立執行個體；<xref:System.ServiceModel.ClientBase%601> 衍生用戶端物件會封裝通道處理站的處理，但在許多案例中，直接使用通道處理站是很自然合理的情況。例如當您想要重複地從現有的處理站建立新的用戶端通道，就是這種情形的常見案例。如果是使用用戶端物件，您可以透過呼叫 <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=fullName> 屬性，從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件取得基礎通道處理站。  
  
 對於通道處理站，請特別記住它們會先針對提供給它們的組態建立用戶端通道的新執行個體，然後才呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=fullName>。一旦呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> \(或 <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=fullName>、<xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=fullName>，或在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件上的任何作業\) 之後，您就無法修改此通道處理站，也無法取得不同服務執行個體的通道，即使您只是要變更目標端點位址也是如此。如果想要使用不同的組態來建立用戶端物件或用戶端通道，您就必須先建立新的通道處理站。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道時各種問題的詳細資訊，請參閱[使用 WCF 用戶端存取服務](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。  
  
 下列兩個小節將說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道物件的建立和使用方式。  
  
#### 建立新的 WCF 用戶端通道物件  
 為了說明用戶端通道的使用方式，請假設已產生下列服務合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 若要連接至 `ISampleService` 服務，請直接搭配通道處理站 \(<xref:System.ServiceModel.ChannelFactory%601>\) 使用產生的合約介面。在建立並設定特定之合約的通道處理站之後，您就可以呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> 方法，傳回可以用來與 `ISampleService` 服務進行通訊的用戶端通道物件。  
  
 當使用含有服務合約介面的 <xref:System.ServiceModel.ChannelFactory%601> 類別時，您必須轉型為 <xref:System.ServiceModel.IClientChannel> 介面，才能明確地開啟、關閉或中止通道。為了讓這個類別更容易使用，Svcutil.exe 工具會另外產生可以實作服務合約介面和 <xref:System.ServiceModel.IClientChannel> 兩者的協助程式介面，讓您可以不用轉型就與用戶端通道基礎結構進行互動。下列程式碼會示範實作前述服務合約之協助程式用戶端通道的定義。  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### 建立新的 WCF 用戶端通道物件  
 若要使用用戶端通道連接至 `ISampleService` 服務，請傳遞合約介面類型做為型別參數，直接搭配通道處理站使用產生的合約介面 \(或是協助程式版本\)。在已建立並設定特定之合約的通道處理站之後，您就可以呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=fullName> 方法，傳回可以用來與 `ISampleService` 服務進行互動的用戶端通道物件。  
  
 建立之後，用戶端通道物件就會實作 <xref:System.ServiceModel.IClientChannel> 和合約介面。因此，您就可以直接使用它們，呼叫與支援該合約之服務進行互動的作業。  
  
 使用用戶端物件和使用用戶端通道物件之間的差別，端視哪種方式對於開發人員而言屬於方便控制和容易使用。大多數習慣使用類別和物件的開發人員會習慣使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件，而不是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端通道。  
  
 如需範例，請參閱 [HOW TO：使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)。