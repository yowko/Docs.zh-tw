---
title: HOW TO：使用 ChannelFactory
description: 瞭解如何建立通道處理站來建立多個通道，以使用 WCF 用戶端來存取服務。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7c87026ca4cf7c739f4615da9bc7f0272a382392
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246658"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="36a0e-103">HOW TO：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="36a0e-103">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="36a0e-104">會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。</span><span class="sxs-lookup"><span data-stu-id="36a0e-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="36a0e-105">建立及使用 ChannelFactory 類別</span><span class="sxs-lookup"><span data-stu-id="36a0e-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="36a0e-106">建立並執行 Windows Communication Foundation （WCF）服務。</span><span class="sxs-lookup"><span data-stu-id="36a0e-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="36a0e-107">如需詳細資訊，請參閱[設計和執行服務](../designing-and-implementing-services.md)、設定[服務](../configuring-services.md)和[裝載服務](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="36a0e-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="36a0e-108">使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約（介面）。</span><span class="sxs-lookup"><span data-stu-id="36a0e-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="36a0e-109">在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。</span><span class="sxs-lookup"><span data-stu-id="36a0e-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36a0e-110">範例</span><span class="sxs-lookup"><span data-stu-id="36a0e-110">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
