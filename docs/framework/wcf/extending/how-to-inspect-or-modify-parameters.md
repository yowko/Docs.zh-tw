---
title: HOW TO：檢查或修改參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 5a15de504a27180c19d3450f7e4ddd490999b916
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651108"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="c0462-102">HOW TO：檢查或修改參數</span><span class="sxs-lookup"><span data-stu-id="c0462-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="c0462-103">您可以檢查或修改傳入或傳出訊息上的 Windows Communication Foundation (WCF) 用戶端物件或 WCF 服務的單一作業的實作<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>介面，並將其插入至用戶端或服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="c0462-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="c0462-104">一般來說，作業行為是用於新增單一作業的參數偵測器；其他行為可用於提供範圍更大之執行階段的簡易存取。</span><span class="sxs-lookup"><span data-stu-id="c0462-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="c0462-105">如需詳細資訊，請參閱 <<c0> [ 擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)並[擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。</span><span class="sxs-lookup"><span data-stu-id="c0462-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="c0462-106">檢查或修改參數</span><span class="sxs-lookup"><span data-stu-id="c0462-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="c0462-107">實作 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="c0462-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="c0462-108">請實作 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (視所需要的範圍而定)，將您的參數偵測器新增至 <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c0462-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="c0462-109">在 <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> 上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 方法之前，請先插入您的行為。</span><span class="sxs-lookup"><span data-stu-id="c0462-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0462-110">如需詳細資訊，請參閱 <<c0> [ 設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="c0462-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0462-111">範例</span><span class="sxs-lookup"><span data-stu-id="c0462-111">Example</span></span>  
 <span data-ttu-id="c0462-112">下列程式碼範例會依序顯示：</span><span class="sxs-lookup"><span data-stu-id="c0462-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="c0462-113">參數偵測器實作。</span><span class="sxs-lookup"><span data-stu-id="c0462-113">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="c0462-114">使用 <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> 插入參數偵測器的行為實作。</span><span class="sxs-lookup"><span data-stu-id="c0462-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c0462-115">在用戶端應用程式中載入及執行端點行為，以在用戶端上插入參數偵測器的組態檔。</span><span class="sxs-lookup"><span data-stu-id="c0462-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c0462-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0462-116">See also</span></span>

- [<span data-ttu-id="c0462-117">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="c0462-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
