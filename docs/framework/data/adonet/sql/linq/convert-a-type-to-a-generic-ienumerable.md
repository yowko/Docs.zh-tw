---
title: 將類型轉換為泛型 IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d75c9b9123b52b3e241bea1bbd1d302c406715e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032704"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>將類型轉換為泛型 IEnumerable
使用 <xref:System.Linq.Enumerable.AsEnumerable%2A> 傳回型別設為泛型 `IEnumerable` 的引數。  
  
## <a name="example"></a>範例  
 在此範例中，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (使用預設泛型 `Query`) 會嘗試將查詢轉換為 SQL，並且在伺服器上執行查詢。 但是，`where` 子句會參考使用者定義的用戶端方法 (`isValidProduct`)，而該方法無法轉換為 SQL。  
  
 解決方案為指定 <xref:System.Collections.Generic.IEnumerable%601> 的用戶端泛型 `where` 實作，以取代泛型 <xref:System.Linq.IQueryable%601>。 您可藉由叫用 (Invoke) <xref:System.Linq.Enumerable.AsEnumerable%2A> 運算子來完成這項作業。  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
