---
title: "HOW TO：檢查或修改參數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：檢查或修改參數
您可以檢查或修改單一作業的傳入或傳出訊息上[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]用戶端物件或[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務，方法是實作<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>介面並將它插入用戶端或服務執行階段。 一般來說，作業行為是用於新增單一作業的參數偵測器；其他行為可用於提供範圍更大之執行階段的簡易存取。 如需詳細資訊，請參閱[擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)和[擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。  
  
### <a name="inspecting-or-modifying-parameters"></a>檢查或修改參數  
  
1.  實作<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>介面。  
  
2.  實作<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>， <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>， <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>或<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName> （視所需要的範圍） 若要將您的參數偵測器新增至<xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=fullName>或<xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=fullName>屬性。  
  
3.  插入您的行為，然後才呼叫<xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=fullName>或<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName>方法<xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>。 如需詳細資訊，請參閱[設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會依序顯示：  
  
-   參數偵測器實作。  
  
-   插入參數偵測器使用的行為實作<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>， <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>，和<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>。  
  
-   在用戶端應用程式中載入及執行端點行為，以在用戶端上插入參數偵測器的組態檔。  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 <!-- TODO: review snippet reference [!code[Interceptors#3](../../../../samples/snippets/common/VS_Snippets_CFX/interceptors/common/client.exe.config#3)]  -->
 <!-- TODO: review snippet reference [!code-csharp[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  -->
 <!-- TODO: review snippet reference [!code-vb[Interceptors#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/client.exe.config#3)]  -->  
  
## <a name="see-also"></a>另請參閱  
 [設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)