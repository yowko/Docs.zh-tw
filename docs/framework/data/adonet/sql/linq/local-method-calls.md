---
title: 區域方法呼叫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781415"
---
# <a name="local-method-calls"></a>區域方法呼叫
區域方法呼叫就是在物件模型 (Object Model) 內執行的呼叫。 遠端方法呼叫則是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 轉譯為 SQL 並傳輸給資料庫引擎進行執行的呼叫。 當無法將呼叫轉譯為[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 時，需要區域方法呼叫。 否則會擲回 <xref:System.InvalidOperationException>。  
  
## <a name="example-1"></a>範例 1  
 在下列範例中，`Order` 類別會對應至 Northwind 範例資料庫中的 Orders 資料表。 本機執行個體方法已加入至這個類別中。  
  
 在查詢 1 中，會在本機執行 `Order` 類別的建構函式。 在查詢 2 中，如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 嘗試將 `LocalInstanceMethod()` 轉譯為 SQL，則嘗試會失敗，而且會擲回 <xref:System.InvalidOperationException> 例外狀況 (Exception)。 但是因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援區域方法呼叫，所以查詢 2 不會擲回例外狀況。  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
