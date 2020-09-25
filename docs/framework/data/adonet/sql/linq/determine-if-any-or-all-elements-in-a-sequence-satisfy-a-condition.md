---
title: 判斷序列中的任何或所有項目是否全都符合條件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 65a9a7cf289c2006bab14cb384efb07eaea7f7a0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194423"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>判斷序列中的任何或所有項目是否全都符合條件

如果序列中所有的項目都符合條件，則 <xref:System.Linq.Enumerable.All%2A> 運算子會傳回 `true`。  
  
 如果序列中有任何項目符合條件，則 <xref:System.Linq.Queryable.Any%2A> 運算子會傳回 `true`。  
  
## <a name="example"></a>範例  

 下列範例會傳回至少有一張訂單的客戶序列。 `Where` / `where` `true` 如果給定的具有 any，子句會評估為 `Customer` `Order` 。  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>範例  

 下列 Visual Basic 程式碼會判斷尚未下單的客戶清單，並且確保該清單中的每位客戶都有一個連絡人名稱。  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>範例  

 下列 C# 範例會傳回其訂單具有以 "C" 開頭之 `ShipCity` 的客戶序列。 傳回的資料中還包含了沒有訂單的客戶  依設計 (， <xref:System.Linq.Queryable.All%2A> 運算子會傳回 `true` 空的序列。使用運算子在主控台輸出中排除沒有訂單的客戶 ) 。 `Count`  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](query-examples.md)
