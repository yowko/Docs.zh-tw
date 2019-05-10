---
title: 了解產生的用戶端程式碼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: dedfa55cb7be7eed396c897dedc6bf375c34436e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626268"
---
# <a name="understanding-generated-client-code"></a>了解產生的用戶端程式碼
[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 會產生用戶端程式碼和用戶端應用程式組態檔，用於建置用戶端應用程式。 本主題將提供產生之程式碼範例的導覽，用於標準服務合約情節。 如需有關如何建置使用產生的程式碼的用戶端應用程式的詳細資訊，請參閱 < [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)。  
  
## <a name="overview"></a>總覽  
 如果您使用 Visual Studio 為您的專案中產生 Windows Communication Foundation (WCF) 用戶端型別時，通常不需要檢查產生的用戶端程式碼。 如果您不是使用為您執行相同服務的開發環境，可以使用如 Svcutil.exe 等工具來產生用戶端程式碼，然後使用該程式碼來開發您的用戶端應用程式。  
  
 由於 Svcutil.exe 有許多選項可修改產生的型別資訊，因此本主題不會討論所有的案例。 然而，下列標準工作包含找出產生的程式碼：  
  
- 識別服務合約介面。  
  
- 用來識別的 WCF 用戶端類別。  
  
- 識別資料型別。  
  
- 識別雙工服務的回呼合約。  
  
- 識別協助程式服務合約通道介面。  
  
### <a name="finding-service-contract-interfaces"></a>尋找服務合約介面  
 如果要找出建立服務合約模型的介面，請搜尋以 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性標示的介面。 由於其他屬性的存在，且這個屬性本身有明確的內容設定，因此常常很難快速找出這個屬性。 請記住，服務合約介面和用戶端合約介面是兩種不同的型別。 下列程式碼範例會顯示原始的服務合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 下列程式碼範例會顯示和 Svcutil.exe 所產生之相同的服務合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 您可以使用產生的服務合約介面，連同<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>類別來建立用來叫用服務作業的 WCF 通道物件。 如需詳細資訊，請參閱[如何：使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)。  
  
### <a name="finding-wcf-client-classes"></a>尋找 WCF 用戶端類別  
 若要找出實作您想要使用的服務合約的 WCF 用戶端類別，搜尋的延伸模組<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>、 型別參數是服務合約介面，您先前位於和延伸該介面。 下列程式碼範例會顯示型別 <xref:System.ServiceModel.ClientBase%601> 的 `ISampleService`類別。  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 您可以使用此 WCF 用戶端類別建立它的新執行個體並呼叫它實作的方法。 這些方法會叫用用於設計及設定互動的服務作業。 如需詳細資訊，請參閱 < [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)。  
  
> [!NOTE]
>  當 SvcUtil.exe 產生 WCF 用戶端類別時，會將 <xref:System.Diagnostics.DebuggerStepThroughAttribute> 加入至用戶端類別，防止偵錯工具逐步執行 WCF 用戶端類別。  
  
### <a name="finding-data-types"></a>尋找資料型別  
 如果要在產生的程式碼中找出資料型別，最基本的機制就是識別合約中指定的型別名稱，然後在程式碼中搜尋該型別宣告。 例如，下列合約指定 `SampleMethod` 可以傳回型別 `microsoft.wcf.documentation.SampleFault`的 SOAP 錯誤。  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 搜尋 `SampleFault` 會找出下列型別宣告。  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 在此情況下，資料型別是由用戶端上特定例外狀況擲回的詳細型別，其中詳細型別參數為 <xref:System.ServiceModel.FaultException%601> 的 `microsoft.wcf.documentation.SampleFault`。 如需資料類型的詳細資訊，請參閱 < [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。 如需有關處理用戶端中的例外狀況的詳細資訊，請參閱[Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)。  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>尋找雙工服務的回呼合約  
 如果您找出合約介面為其指定 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> 屬性值的服務合約，該合約就會指定雙工合約。 雙工合約需要用戶端應用程式建立回呼類別，實作回呼合約並將該類別的執行個體傳遞至用來與服務通訊的 <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> 或 <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> 。 如需雙工用戶端的詳細資訊，請參閱[How to:使用雙工合約存取服務](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)。  
  
 下列合約會指定型別 `SampleDuplexHelloCallback`的回呼合約。  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 搜尋該回呼合約會找出下列用戶端應用程式必須實作的介面。  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>尋找服務合約通道介面  
 當使用含有服務合約介面的 <xref:System.ServiceModel.ChannelFactory> 類別時，您必須轉換為 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> 介面，以明確開啟、關閉或中止通道。 為了讓這個類別更容易使用，Svcutil.exe 工具會另外產生可以實作服務合約介面和 <xref:System.ServiceModel.IClientChannel> 兩者的協助程式介面，讓您可以不用轉型就與用戶端通道基礎結構進行互動。 下列程式碼會示範實作前述服務合約之協助程式用戶端通道的定義。  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>另請參閱

- [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)
