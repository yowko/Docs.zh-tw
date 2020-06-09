---
title: HOW TO：使用合約介面來建立服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597159"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="1a5fa-102">HOW TO：使用合約介面來建立服務</span><span class="sxs-lookup"><span data-stu-id="1a5fa-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="1a5fa-103">建立 Windows Communication Foundation （WCF）合約的慣用方法是使用介面。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="1a5fa-104">此合約可指定存取服務提供之作業時所需的訊息集合與結構。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="1a5fa-105">此介面可將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面，並將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到您想要公開的方法上，藉此定義輸入與輸出類型。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="1a5fa-106">如需服務合約的詳細資訊，請參閱[設計服務合約](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="1a5fa-107">使用介面來建立 WCF 合約</span><span class="sxs-lookup"><span data-stu-id="1a5fa-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="1a5fa-108">使用 Visual Basic、c # 或其他任何 common language runtime 語言來建立新的介面。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="1a5fa-109">將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="1a5fa-110">在介面中定義方法。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="1a5fa-111">將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用至必須公開為公用 WCF 合約一部分的每個方法。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a5fa-112">範例</span><span class="sxs-lookup"><span data-stu-id="1a5fa-112">Example</span></span>  
 <span data-ttu-id="1a5fa-113">下列程式碼範例會顯示可定義服務合約的介面。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="1a5fa-114">已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="1a5fa-115">如需此訊息模式的詳細資訊，請參閱[如何：建立要求-回復合約](how-to-create-a-request-reply-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="1a5fa-116">您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="1a5fa-117">如需更多範例，請參閱[如何：建立單向合約](how-to-create-a-one-way-contract.md)和[如何：建立雙工合約](how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="1a5fa-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5fa-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a5fa-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
