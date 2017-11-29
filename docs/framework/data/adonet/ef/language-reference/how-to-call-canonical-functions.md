---
title: "如何：呼叫標準函式"
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
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26bd528a7c2ad77cb801eb294c34e43c60d2bf76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-canonical-functions"></a>如何：呼叫標準函式
<xref:System.Data.Objects.EntityFunctions> 類別包含可公開標準函式以用於 LINQ to Entities 查詢的方法。 如需標準函式的資訊，請參閱[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> 類別中的 <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> 和 <xref:System.Data.Objects.EntityFunctions> 方法沒有對等的標準函式。  
  
 標準函式 (亦稱為彙總標準函式) 可直接叫用，它們會執行值集的計算，並傳回單一值。 呼叫的其他標準函式則做為 LINQ to Entities 查詢的一部份。 若要直接呼叫彙總函式，您必須將 <xref:System.Data.Objects.ObjectQuery%601> 傳遞至函式。 如需詳細資訊，請參閱下列第二個範例。  
  
 您可以在 LINQ to Entities 查詢中，使用 Common Language Runtime (CLR) 方法呼叫部分標準函式。 如需 CLR 方法對應到標準函式的清單，請參閱[標準函式對應的 CLR 方法](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)。 範例執行 LINQ to Entities 查詢，使用 <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> 方法，傳回 `SellEndDate` 和 `SellStartDate` 之間的差距小於 365 天的所有產品：  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>範例  
 下列範例會使用[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)。 範例直接呼叫彙總 <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> 方法，以傳回 `SalesOrderHeader` 小計的標準差。 請注意，<xref:System.Data.Objects.ObjectQuery%601> 已傳遞至函式，函式允許其接受呼叫時，不必成為 LINQ to Entities 查詢的一部份。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Entities 查詢中呼叫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
