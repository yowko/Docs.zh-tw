---
title: "HOW TO：檢查及修改服務中的訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e1c6c6417a9aef1995377657aadc9def7ae4d13
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="02ad1-102">HOW TO：檢查及修改服務中的訊息</span><span class="sxs-lookup"><span data-stu-id="02ad1-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="02ad1-103">您可實作 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 並將它插入服務執行階段，以檢查或修改 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> 用戶端內傳入或傳出的訊息。</span><span class="sxs-lookup"><span data-stu-id="02ad1-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="02ad1-104">如需詳細資訊，請參閱[擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。</span><span class="sxs-lookup"><span data-stu-id="02ad1-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="02ad1-105">服務上對等的功能為 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="02ad1-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="02ad1-106">檢查或修改訊息</span><span class="sxs-lookup"><span data-stu-id="02ad1-106">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="02ad1-107">實作 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="02ad1-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="02ad1-108">根據您要輕鬆插入服務訊息偵測器的範圍，決定實作 <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>或  介面。</span><span class="sxs-lookup"><span data-stu-id="02ad1-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3.  <span data-ttu-id="02ad1-109">在 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 上呼叫 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 方法之前，請先插入您的行為。</span><span class="sxs-lookup"><span data-stu-id="02ad1-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="02ad1-110">如需詳細資訊，請參閱[設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="02ad1-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ad1-111">範例</span><span class="sxs-lookup"><span data-stu-id="02ad1-111">Example</span></span>  
 <span data-ttu-id="02ad1-112">下列程式碼範例會依序顯示：</span><span class="sxs-lookup"><span data-stu-id="02ad1-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="02ad1-113">服務偵測器實作。</span><span class="sxs-lookup"><span data-stu-id="02ad1-113">A service inspector implementation.</span></span>  
  
-   <span data-ttu-id="02ad1-114">插入偵測器的服務行為。</span><span class="sxs-lookup"><span data-stu-id="02ad1-114">A service behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="02ad1-115">在服務應用程式中載入及執行此行為的組態檔。</span><span class="sxs-lookup"><span data-stu-id="02ad1-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="02ad1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02ad1-116">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="02ad1-117">設定與擴充執行階段行為</span><span class="sxs-lookup"><span data-stu-id="02ad1-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
