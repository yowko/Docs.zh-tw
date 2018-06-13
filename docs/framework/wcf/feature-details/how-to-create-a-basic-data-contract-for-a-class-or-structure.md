---
title: HOW TO：建立類別或結構的基本資料合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: bb2cebabc8e51870398689ea032d27c72f0503b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490064"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="35004-102">HOW TO：建立類別或結構的基本資料合約</span><span class="sxs-lookup"><span data-stu-id="35004-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="35004-103">本主題將示範使用類別或結構來建立資料合約的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="35004-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="35004-104">如需資料合約和使用方式的詳細資訊，請參閱[使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="35004-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="35004-105">逐步解說的步驟建立基本的 Windows Communication Foundation (WCF) 服務和用戶端的教學課程中，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="35004-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="35004-106">基本服務和用戶端所組成的工作範例應用程式，請參閱[基本資料合約](../../../../docs/framework/wcf/samples/basic-data-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="35004-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="35004-107">建立類別或結構的基本資料合約</span><span class="sxs-lookup"><span data-stu-id="35004-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="35004-108">請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類別，以宣告型別具有資料合約。</span><span class="sxs-lookup"><span data-stu-id="35004-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="35004-109">請注意，所有公用型別 (包括不含屬性的公用型別) 都是可序列化的。</span><span class="sxs-lookup"><span data-stu-id="35004-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="35004-110">如果沒有 <xref:System.Runtime.Serialization.DataContractSerializer> 屬性，<xref:System.Runtime.Serialization.DataContractAttribute> 會推斷資料合約。</span><span class="sxs-lookup"><span data-stu-id="35004-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="35004-111">如需詳細資訊，請參閱[可序列化型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="35004-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="35004-112">藉由將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute) 套用至各個成員，定義序列化的成員 (屬性 (Property)、欄位或事件)。</span><span class="sxs-lookup"><span data-stu-id="35004-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="35004-113">這些成員稱為資料成員。</span><span class="sxs-lookup"><span data-stu-id="35004-113">These members are called data members.</span></span> <span data-ttu-id="35004-114">根據預設，所有公用型別都是可序列化的。</span><span class="sxs-lookup"><span data-stu-id="35004-114">By default, all public types are serializable.</span></span> <span data-ttu-id="35004-115">如需詳細資訊，請參閱[可序列化型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="35004-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35004-116">您可以將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至私用欄位，造成資料對他人公開。</span><span class="sxs-lookup"><span data-stu-id="35004-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="35004-117">請確定成員沒有包含敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="35004-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35004-118">範例</span><span class="sxs-lookup"><span data-stu-id="35004-118">Example</span></span>  
 <span data-ttu-id="35004-119">下列範例說明如何將 `Person` 和 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類別和其成員，以建立 <xref:System.Runtime.Serialization.DataMemberAttribute> 型別的資料合約。</span><span class="sxs-lookup"><span data-stu-id="35004-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="35004-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35004-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="35004-121">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="35004-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="35004-122">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="35004-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="35004-123">快速入門</span><span class="sxs-lookup"><span data-stu-id="35004-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
