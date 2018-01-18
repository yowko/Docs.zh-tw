---
title: "判斷序列中的任何或所有項目是否全都符合條件"
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
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b9b79915e94ed1015c7869692647c10da58f60
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>判斷序列中的任何或所有項目是否全都符合條件
如果序列中所有的項目都符合條件，則 <xref:System.Linq.Enumerable.All%2A> 運算子會傳回 `true`。  
  
 如果序列中有任何項目符合條件，則 <xref:System.Linq.Queryable.Any%2A> 運算子會傳回 `true`。  
  
## <a name="example"></a>範例  
 下列範例會傳回至少有一張訂單的客戶序列。 `Where` / `where` When 子句評估為`true`如果給定`Customer`有任何`Order`。  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>範例  
 下列 Visual Basic 程式碼會判斷尚未下單的客戶清單，並且確保該清單中的每位客戶都有一個連絡人名稱。  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>範例  
 下列 C# 範例會傳回其訂單具有以 "C" 開頭之 `ShipCity` 的客戶序列。 傳回的資料中還包含了沒有訂單的客戶  (根據設計，<xref:System.Linq.Queryable.All%2A> 運算子會針對空序列傳回 `true`)。使用 `Count` 運算子，可以在主控台輸出中排除沒有訂單的客戶。  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
