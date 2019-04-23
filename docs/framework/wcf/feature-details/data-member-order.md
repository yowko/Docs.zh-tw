---
title: 資料成員順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: c78cc682c0776bfb0ce09dec7ba1ff8cab504285
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198565"
---
# <a name="data-member-order"></a><span data-ttu-id="99369-102">資料成員順序</span><span class="sxs-lookup"><span data-stu-id="99369-102">Data Member Order</span></span>
<span data-ttu-id="99369-103">在某些應用程式中，知道來自各個資料成員之資料的傳送順序或是資料的預期收到順序是十分有用的 (例如，資料出現在序列化 XML 中的順序)。</span><span class="sxs-lookup"><span data-stu-id="99369-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="99369-104">有時候可能需要變更這個順序。</span><span class="sxs-lookup"><span data-stu-id="99369-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="99369-105">本主題將說明排序規則。</span><span class="sxs-lookup"><span data-stu-id="99369-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="99369-106">基本規則</span><span class="sxs-lookup"><span data-stu-id="99369-106">Basic Rules</span></span>  
 <span data-ttu-id="99369-107">資料排序的基本規則包括：</span><span class="sxs-lookup"><span data-stu-id="99369-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="99369-108">如果資料合約類型屬於繼承階層的一部分，則其基底類型的資料成員的順序一定會是最前面。</span><span class="sxs-lookup"><span data-stu-id="99369-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="99369-109">順序接著為目前類型的資料成員，該成員不具有以字母順序顯示之 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性 (Attribute) 集的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="99369-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="99369-110">順序接著為不具有 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性 (Attribute) 集之 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property) 的任何資料成員。</span><span class="sxs-lookup"><span data-stu-id="99369-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="99369-111">這些成員會先依據 `Order` 屬性的值排序，如果有一個以上的成員擁有特定的 `Order` 值才會以字母排序。</span><span class="sxs-lookup"><span data-stu-id="99369-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="99369-112">Order 屬性值可以略過。</span><span class="sxs-lookup"><span data-stu-id="99369-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="99369-113">透過呼叫 <xref:System.String.CompareOrdinal%2A> 方法，即可建立字母順序。</span><span class="sxs-lookup"><span data-stu-id="99369-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="99369-114">範例</span><span class="sxs-lookup"><span data-stu-id="99369-114">Examples</span></span>  
 <span data-ttu-id="99369-115">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="99369-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="99369-116">產生的 XML 如下所示。</span><span class="sxs-lookup"><span data-stu-id="99369-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99369-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99369-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="99369-118">資料合約等價</span><span class="sxs-lookup"><span data-stu-id="99369-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="99369-119">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="99369-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
