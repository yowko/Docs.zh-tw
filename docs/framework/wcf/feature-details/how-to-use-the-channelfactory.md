---
title: 作法：使用 ChannelFactory
description: 瞭解如何建立通道處理站，以建立多個通道以使用 WCF 用戶端來存取服務。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: dd767443fefb16ebc02300bffa4264357f12c3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280581"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="1974f-103">作法：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="1974f-103">How to: Use the ChannelFactory</span></span>

<span data-ttu-id="1974f-104">會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。</span><span class="sxs-lookup"><span data-stu-id="1974f-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="1974f-105">建立及使用 ChannelFactory 類別</span><span class="sxs-lookup"><span data-stu-id="1974f-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="1974f-106">建立並執行 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="1974f-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="1974f-107">如需詳細資訊，請參閱 [設計和執行服務](../designing-and-implementing-services.md)、設定 [服務](../configuring-services.md)和 [裝載服務](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1974f-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="1974f-108">使用 [ [System.servicemodel 中繼資料公用程式] 工具 ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) ，為用戶端產生合約 (介面) 。</span><span class="sxs-lookup"><span data-stu-id="1974f-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="1974f-109">在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。</span><span class="sxs-lookup"><span data-stu-id="1974f-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1974f-110">範例</span><span class="sxs-lookup"><span data-stu-id="1974f-110">Example</span></span>  

 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
