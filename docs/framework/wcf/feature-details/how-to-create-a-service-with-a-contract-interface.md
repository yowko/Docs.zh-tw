---
title: HOW TO：使用合約介面來建立服務
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b4af593edd355ed89da8c5b2c79a4c029b966fe4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="11ce1-102">HOW TO：使用合約介面來建立服務</span><span class="sxs-lookup"><span data-stu-id="11ce1-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="11ce1-103">建立 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 合約的慣用方式就是使用介面。</span><span class="sxs-lookup"><span data-stu-id="11ce1-103">The preferred way to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="11ce1-104">此合約可指定存取服務提供之作業時所需的訊息集合與結構。</span><span class="sxs-lookup"><span data-stu-id="11ce1-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="11ce1-105">此介面可將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面，並將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到您想要公開的方法上，藉此定義輸入與輸出類型。</span><span class="sxs-lookup"><span data-stu-id="11ce1-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="11ce1-106">如需服務合約的詳細資訊，請參閱[設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="11ce1-106">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="11ce1-107">使用介面來建立 WCF 合約</span><span class="sxs-lookup"><span data-stu-id="11ce1-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="11ce1-108">建立新的介面，使用 Visual Basic、 C# 中，或任何其他 common language runtime 語言。</span><span class="sxs-lookup"><span data-stu-id="11ce1-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="11ce1-109">將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面。</span><span class="sxs-lookup"><span data-stu-id="11ce1-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="11ce1-110">在介面中定義方法。</span><span class="sxs-lookup"><span data-stu-id="11ce1-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="11ce1-111">將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個方法 (必須當成公開 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 合約的一部分加以公開) 上。</span><span class="sxs-lookup"><span data-stu-id="11ce1-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11ce1-112">範例</span><span class="sxs-lookup"><span data-stu-id="11ce1-112">Example</span></span>  
 <span data-ttu-id="11ce1-113">下列程式碼範例會顯示可定義服務合約的介面。</span><span class="sxs-lookup"><span data-stu-id="11ce1-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="11ce1-114">已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。</span><span class="sxs-lookup"><span data-stu-id="11ce1-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="11ce1-115">如需有關此訊息模式的詳細資訊，請參閱[How to： 建立要求-回覆合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="11ce1-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="11ce1-116">您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。</span><span class="sxs-lookup"><span data-stu-id="11ce1-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="11ce1-117">如需其他範例，請參閱[How to： 建立單向合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)和[How to： 建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="11ce1-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ce1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11ce1-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
