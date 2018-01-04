---
title: "HOW TO：使用 ChannelFactory"
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
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 644160f11bd743a0c1d598cc01b3e365adea5c56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="7b176-102">HOW TO：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="7b176-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="7b176-103">會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。</span><span class="sxs-lookup"><span data-stu-id="7b176-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="7b176-104">建立及使用 ChannelFactory 類別</span><span class="sxs-lookup"><span data-stu-id="7b176-104">To create and use the ChannelFactory class</span></span>  
  
1.  <span data-ttu-id="7b176-105">建置及執行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="7b176-105">Build and run an [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7b176-106">[設計和實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)，[設定服務](../../../../docs/framework/wcf/configuring-services.md)，和[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b176-106"> [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2.  <span data-ttu-id="7b176-107">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="7b176-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3.  <span data-ttu-id="7b176-108">在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。</span><span class="sxs-lookup"><span data-stu-id="7b176-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b176-109">範例</span><span class="sxs-lookup"><span data-stu-id="7b176-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
