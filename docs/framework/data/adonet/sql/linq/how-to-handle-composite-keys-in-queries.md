---
title: HOW TO：在查詢中處理複合索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 2621ab4db207d1b868fbe3778c30c744201b0506
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135248"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>HOW TO：在查詢中處理複合索引鍵
有些運算子只能取用一個引數。 如果引數必須包括資料庫中的多個資料行，則必須建立匿名型別來表示此項組合。  
  
## <a name="example"></a>範例  
 下列範例顯示叫用 (Invoke) `GroupBy` 運算子的查詢，這個運算子只可以取用一個 `key` 引數。  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>範例  
 聯結 (Join) 的情況也相同，如下列範例所示：  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
