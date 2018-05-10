---
title: HOW TO：檢查或修改參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 1b825ff795f4db9d570420b187b8fedd041ddd3d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-inspect-or-modify-parameters"></a>HOW TO：檢查或修改參數
您可以檢查或修改傳入或傳出的訊息上的 Windows Communication Foundation (WCF) 用戶端物件或 WCF 服務的單一作業實作<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>介面並將它插入用戶端或服務執行階段。 一般來說，作業行為是用於新增單一作業的參數偵測器；其他行為可用於提供範圍更大之執行階段的簡易存取。 如需詳細資訊，請參閱[擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)和[擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。  
  
### <a name="inspecting-or-modifying-parameters"></a>檢查或修改參數  
  
1.  實作 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> 介面。  
  
2.  請實作 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (視所需要的範圍而定)，將您的參數偵測器新增至 <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> 屬性。  
  
3.  在 <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> 上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 方法之前，請先插入您的行為。 如需詳細資訊，請參閱[設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例會依序顯示：  
  
-   參數偵測器實作。  
  
-   使用 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> 插入參數偵測器的行為實作。  
  
-   在用戶端應用程式中載入及執行端點行為，以在用戶端上插入參數偵測器的組態檔。  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>另請參閱  
 [使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
