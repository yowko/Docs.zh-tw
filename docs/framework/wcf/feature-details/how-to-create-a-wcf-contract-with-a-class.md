---
title: HOW TO：使用類別建立 Windows Communication Foundation 合約
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54d5e1328482fc7d0c1ee33918ffae6bf7195db9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="ec97d-102">HOW TO：使用類別建立 Windows Communication Foundation 合約</span><span class="sxs-lookup"><span data-stu-id="ec97d-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="ec97d-103">最好是使用介面來建立 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 合約。</span><span class="sxs-lookup"><span data-stu-id="ec97d-103">The preferred way of creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="ec97d-104">如需詳細資訊，請參閱[如何： 定義服務合約](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="ec97d-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="ec97d-105">另一個方式就像這裡所略述的步驟，先建立一個類別，然後將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性直接套用至該類別，並將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用該類別中屬於合約部分的各個方法。</span><span class="sxs-lookup"><span data-stu-id="ec97d-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ec97d-106">`[ServiceContract]` 和 `[ServiceContractAttribute]` 會執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="ec97d-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="ec97d-107">同樣的情況也適用於 `[OperationContract]` 和 `[OperationContractAttribute]`。</span><span class="sxs-lookup"><span data-stu-id="ec97d-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="ec97d-108">在每個情況下，前者都是後者的簡寫。</span><span class="sxs-lookup"><span data-stu-id="ec97d-108">In each case the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="ec97d-109">如需服務合約的詳細資訊，請參閱[設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ec97d-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="ec97d-110">以類別建立 Windows Communication Foundation 合約</span><span class="sxs-lookup"><span data-stu-id="ec97d-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="ec97d-111">建立新的類別，使用 Visual Basic、 C# 中，或任何其他 common language runtime 語言。</span><span class="sxs-lookup"><span data-stu-id="ec97d-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="ec97d-112">將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用至該類別。</span><span class="sxs-lookup"><span data-stu-id="ec97d-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="ec97d-113">建立類別內的方法。</span><span class="sxs-lookup"><span data-stu-id="ec97d-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="ec97d-114">將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個方法 (必須當成公開 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 合約的一部分加以公開) 上。</span><span class="sxs-lookup"><span data-stu-id="ec97d-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec97d-115">範例</span><span class="sxs-lookup"><span data-stu-id="ec97d-115">Example</span></span>  
 <span data-ttu-id="ec97d-116">下列程式碼範例會示範定義服務合約的類別。</span><span class="sxs-lookup"><span data-stu-id="ec97d-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="ec97d-117">已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。</span><span class="sxs-lookup"><span data-stu-id="ec97d-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="ec97d-118">如需有關此訊息模式的詳細資訊，請參閱[How to： 建立要求-回覆合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="ec97d-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="ec97d-119">您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。</span><span class="sxs-lookup"><span data-stu-id="ec97d-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="ec97d-120">如需其他範例，請參閱[How to： 建立單向合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)和[How to： 建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="ec97d-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec97d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec97d-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
