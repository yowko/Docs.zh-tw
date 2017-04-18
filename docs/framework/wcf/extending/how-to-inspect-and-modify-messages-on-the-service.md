---
title: "HOW TO：檢查及修改服務中的訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# HOW TO：檢查及修改服務中的訊息
您可以檢查或修改傳入或傳出的訊息[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]用戶端藉由實作<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>並將它插入服務執行階段。 如需詳細資訊，請參閱[擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。 在服務上對等的功能是<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>。  
  
### <a name="to-inspect-or-modify-messages"></a>檢查或修改訊息  
  
1.  實作<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>介面。  
  
2.  實作<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=fullName>， <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>，或<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName>介面取決於您要輕鬆插入服務訊息偵測器的範圍而定。  
  
3.  插入您的行為，然後才呼叫<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName>方法<xref:System.ServiceModel.ServiceHost?displayProperty=fullName>。 如需詳細資訊，請參閱[設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會依序顯示：  
  
-   服務偵測器實作。  
  
-   插入偵測器的服務行為。  
  
-   在服務應用程式中載入及執行此行為的組態檔。  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code[Interceptors#9](../../../../samples/snippets/common/VS_Snippets_CFX/interceptors/common/hostapplication.exe.config#9)]
 [!code-csharp[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]
 [!code-vb[Interceptors#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>   
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>   
 [設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)