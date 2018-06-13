---
title: 將序列轉換為泛型 List
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: 0a02e8b9b07121b27639acc64d8898068e3bf4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361798"
---
# <a name="convert-a-sequence-to-a-generic-list"></a>將序列轉換為泛型 List
使用 <xref:System.Linq.Enumerable.ToList%2A> 從序列建立泛型清單。  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Linq.Enumerable.ToList%2A> 立即將查詢評估為泛型 <xref:System.Collections.Generic.List%601>。  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
