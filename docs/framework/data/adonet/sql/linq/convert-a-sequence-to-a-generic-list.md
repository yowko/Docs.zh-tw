---
title: 將序列轉換為泛型 List
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: 79e3ddaff0234dfb5f91e36bacd3279afa9ec265
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164385"
---
# <a name="convert-a-sequence-to-a-generic-list"></a>將序列轉換為泛型 List

使用 <xref:System.Linq.Enumerable.ToList%2A> 從序列建立泛型清單。  
  
## <a name="example"></a>範例  

 下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 立即將查詢評估為泛型 <xref:System.Collections.Generic.List%601>。  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](query-examples.md)
