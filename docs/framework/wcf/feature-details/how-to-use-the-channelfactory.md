---
title: HOW TO：使用 ChannelFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298847"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="8a229-102">HOW TO：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="8a229-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="8a229-103">會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。</span><span class="sxs-lookup"><span data-stu-id="8a229-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="8a229-104">建立及使用 ChannelFactory 類別</span><span class="sxs-lookup"><span data-stu-id="8a229-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="8a229-105">建置並執行 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="8a229-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="8a229-106">如需詳細資訊，請參閱[設計與實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)， [Configuring](../../../../docs/framework/wcf/configuring-services.md)，並[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8a229-106">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2. <span data-ttu-id="8a229-107">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="8a229-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="8a229-108">在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。</span><span class="sxs-lookup"><span data-stu-id="8a229-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a229-109">範例</span><span class="sxs-lookup"><span data-stu-id="8a229-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
