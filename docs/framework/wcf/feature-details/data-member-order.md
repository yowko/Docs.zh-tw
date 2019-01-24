---
title: 資料成員順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 93ec81d94d8133fc5a6d71d7f1b57b2e9a6aad21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659627"
---
# <a name="data-member-order"></a>資料成員順序
在某些應用程式中，知道來自各個資料成員之資料的傳送順序或是資料的預期收到順序是十分有用的 (例如，資料出現在序列化 XML 中的順序)。 有時候可能需要變更這個順序。 本主題將說明排序規則。  
  
## <a name="basic-rules"></a>基本規則  
 資料排序的基本規則包括：  
  
-   如果資料合約類型屬於繼承階層的一部分，則其基底類型的資料成員的順序一定會是最前面。  
  
-   順序接著為目前類型的資料成員，該成員不具有以字母順序顯示之 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性 (Attribute) 集的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property)。  
  
-   順序接著為不具有 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性 (Attribute) 集之 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property) 的任何資料成員。 這些成員會先依據 `Order` 屬性的值排序，如果有一個以上的成員擁有特定的 `Order` 值才會以字母排序。 Order 屬性值可以略過。  
  
 透過呼叫 <xref:System.String.CompareOrdinal%2A> 方法，即可建立字母順序。  
  
## <a name="examples"></a>範例  
 請考慮下列程式碼：  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 產生的 XML 如下所示。  
  
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
  
## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
