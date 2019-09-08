---
title: 作法：在查詢中處理複合索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: a6c6e7d1c1d29a049b50f4ea9d70ef5cd9e89a44
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793578"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>作法：在查詢中處理複合索引鍵
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

- [查詢概念](query-concepts.md)
