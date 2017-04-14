---
title: "了解產生的用戶端程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 了解產生的用戶端程式碼
[ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 會產生用戶端程式碼和用戶端應用程式組態檔，用於建置用戶端應用程式。 本主題將提供產生之程式碼範例的導覽，用於標準服務合約情節。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 使用產生之程式碼建置用戶端應用程式的詳細資訊，請參閱 [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)。  
  
## 概觀  
 如果您使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 為您的專案產生 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端類型，通常不需要檢查產生的用戶端程式碼。 如果您不是使用為您執行相同服務的開發環境，可以使用如 Svcutil.exe 等工具來產生用戶端程式碼，然後使用該程式碼來開發您的用戶端應用程式。  
  
 由於 Svcutil.exe 有許多選項可修改產生的型別資訊，因此本主題不會討論所有的案例。 然而，下列標準工作包含找出產生的程式碼：  
  
-   識別服務合約介面。  
  
-   識別 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別。  
  
-   識別資料型別。  
  
-   識別雙工服務的回呼合約。  
  
-   識別協助程式服務合約通道介面。  
  
### 尋找服務合約介面  
 如果要找出建立服務合約模型的介面，請搜尋以 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName> 屬性標示的介面。 由於其他屬性的存在，且這個屬性本身有明確的內容設定，因此常常很難快速找出這個屬性。 請記住，服務合約介面和用戶端合約介面是兩種不同的型別。 下列程式碼範例會顯示原始的服務合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 下列程式碼範例會顯示和 Svcutil.exe 所產生之相同的服務合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 您可以使用產生的服務合約介面以及 <xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> 類別，來建立叫用服務作業的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道物件。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [HOW TO：使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### 尋找 WCF 用戶端類別  
 如果要找出實作您要使用之服務合約的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別，請搜尋 <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName> 的延伸，其中型別參數是您之前找出且延伸該介面的服務合約介面。 下列程式碼範例會顯示型別 <xref:System.ServiceModel.ClientBase%601> 的 `ISampleService` 類別。  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 您可以使用這個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別，方法是建立它的新執行個體並呼叫它實作的方法。 這些方法會叫用用於設計及設定互動的服務作業。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  當 SvcUtil.exe 產生 WCF 用戶端類別時，會將 <xref:System.Diagnostics.DebuggerStepThroughAttribute> 加入至用戶端類別，防止偵錯工具逐步執行 WCF 用戶端類別。  
  
### 尋找資料型別  
 如果要在產生的程式碼中找出資料型別，最基本的機制就是識別合約中指定的型別名稱，然後在程式碼中搜尋該型別宣告。 例如，下列合約指定 `SampleMethod` 可以傳回型別 `microsoft.wcf.documentation.SampleFault` 的 SOAP 錯誤。  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 搜尋 `SampleFault` 會找出下列型別宣告。  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 在此情況下，資料型別是由用戶端上特定例外狀況擲回的詳細型別，其中詳細型別參數為 <xref:System.ServiceModel.FaultException%601> 的 `microsoft.wcf.documentation.SampleFault`。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 資料型別的詳細資訊，請參閱 [指定服務合約中的資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]處理用戶端中例外狀況的詳細資訊，請參閱[傳送和接收錯誤](../../../../docs/framework/wcf/sending-and-receiving-faults.md)。  
  
### 尋找雙工服務的回呼合約  
 如果您找出合約介面為其指定 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=fullName> 屬性值的服務合約，該合約就會指定雙工合約。 雙工合約需要用戶端應用程式建立回呼類別，實作回呼合約並將該類別的執行個體傳遞至用來與服務通訊的 <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=fullName> 或 <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=fullName>。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]雙工用戶端的詳細資訊，請參閱[HOW TO：使用雙工合約存取服務](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)。  
  
 下列合約會指定型別 `SampleDuplexHelloCallback` 的回呼合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 搜尋該回呼合約會找出下列用戶端應用程式必須實作的介面。  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### 尋找服務合約通道介面  
 當使用含有服務合約介面的 <xref:System.ServiceModel.ChannelFactory> 類別時，您必須轉換為 <xref:System.ServiceModel.IClientChannel?displayProperty=fullName> 介面，以明確開啟、關閉或中止通道。 為了讓這個類別更容易使用，Svcutil.exe 工具會另外產生可以實作服務合約介面和 <xref:System.ServiceModel.IClientChannel> 兩者的協助程式介面，讓您可以不用轉型就與用戶端通道基礎結構進行互動。 下列程式碼會示範實作前述服務合約之協助程式用戶端通道的定義。  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## 請參閱  
 [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)