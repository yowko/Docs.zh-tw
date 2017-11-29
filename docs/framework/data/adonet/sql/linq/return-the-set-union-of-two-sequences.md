---
title: "傳回兩個序列的集合聯集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 865aa82ebc119a3952124a93f9042c2732e3ab48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-union-of-two-sequences"></a>傳回兩個序列的集合聯集
使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Linq.Queryable.Union%2A> 傳回 `Customers` 或 `Employees` 所在的所有國家/地區序列。  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、<xref:System.Linq.Queryable.Union%2A>運算子 （semantics） 定義為未排序串連 (有效的結果`UNION ALL`SQL 中的子句)。  
  
## <a name="see-also"></a>另請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
