---
title: "串連兩個序列"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a73ace484c3ca519f250069063a9222b75ef6c17
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="concatenate-two-sequences"></a>串連兩個序列
使用 <xref:System.Linq.Queryable.Concat%2A> 運算子可串連兩個序列。  
  
 <xref:System.Linq.Queryable.Concat%2A> 運算子是針對已排序的多重集 (Multiset) 所定義，其中接收者和引數的順序相同。  
  
 產生結果前的最後一個步驟就是在 SQL 中進行排序。 基於這個理由，會使用 <xref:System.Linq.Queryable.Concat%2A> 實作 `UNION ALL` 運算子，但不保留其引數的順序。 若要確保結果的排序正確無誤，請務必明確地將結果排序。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Linq.Queryable.Concat%2A> 傳回所有 `Customer` 和 `Employee` 電話及傳真號碼的序列。  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Linq.Queryable.Concat%2A> 傳回所有 `Customer` 和 `Employee` 姓名及電話號碼對應的序列。  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
