---
title: "資料成員順序"
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
helpviewer_keywords: data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06b311f0ca8e9b0a298cd1d9a5e87ff96d13a787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="data-member-order"></a><span data-ttu-id="7a82d-102">資料成員順序</span><span class="sxs-lookup"><span data-stu-id="7a82d-102">Data Member Order</span></span>
<span data-ttu-id="7a82d-103">在某些應用程式中，知道來自各個資料成員之資料的傳送順序或是資料的預期收到順序是十分有用的 (例如，資料出現在序列化 XML 中的順序)。</span><span class="sxs-lookup"><span data-stu-id="7a82d-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="7a82d-104">有時候可能需要變更這個順序。</span><span class="sxs-lookup"><span data-stu-id="7a82d-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="7a82d-105">本主題將說明排序規則。</span><span class="sxs-lookup"><span data-stu-id="7a82d-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="7a82d-106">基本規則</span><span class="sxs-lookup"><span data-stu-id="7a82d-106">Basic Rules</span></span>  
 <span data-ttu-id="7a82d-107">資料排序的基本規則包括：</span><span class="sxs-lookup"><span data-stu-id="7a82d-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="7a82d-108">如果資料合約類型屬於繼承階層的一部分，則其基底類型的資料成員的順序一定會是最前面。</span><span class="sxs-lookup"><span data-stu-id="7a82d-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="7a82d-109">順序接著為目前類型的資料成員，該成員不具有以字母順序顯示之 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性 (Attribute) 集的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="7a82d-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="7a82d-110">順序接著為不具有 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性 (Attribute) 集之 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property) 的任何資料成員。</span><span class="sxs-lookup"><span data-stu-id="7a82d-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="7a82d-111">這些成員會先依據 `Order` 屬性的值排序，如果有一個以上的成員擁有特定的 `Order` 值才會以字母排序。</span><span class="sxs-lookup"><span data-stu-id="7a82d-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="7a82d-112">Order 屬性值可以略過。</span><span class="sxs-lookup"><span data-stu-id="7a82d-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="7a82d-113">透過呼叫 <xref:System.String.CompareOrdinal%2A> 方法，即可建立字母順序。</span><span class="sxs-lookup"><span data-stu-id="7a82d-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7a82d-114">範例</span><span class="sxs-lookup"><span data-stu-id="7a82d-114">Examples</span></span>  
 <span data-ttu-id="7a82d-115">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7a82d-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="7a82d-116">產生的 XML 如下所示。</span><span class="sxs-lookup"><span data-stu-id="7a82d-116">The XML produced is similar to the following.</span></span>  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a82d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a82d-117">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [<span data-ttu-id="7a82d-118">資料合約等價</span><span class="sxs-lookup"><span data-stu-id="7a82d-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="7a82d-119">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="7a82d-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
