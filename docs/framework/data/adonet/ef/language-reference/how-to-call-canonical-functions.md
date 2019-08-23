---
title: 作法：呼叫標準函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 01a638d494b988e29ccf07763a7e0aecf54cc11c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936060"
---
# <a name="how-to-call-canonical-functions"></a>HOW TO：呼叫標準函式
<xref:System.Data.Objects.EntityFunctions> 類別包含可公開標準函式以用於 LINQ to Entities 查詢的方法。 如需標準函式的資訊，請參閱[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。  
  
> [!NOTE]
> <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> 類別中的 <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> 和 <xref:System.Data.Objects.EntityFunctions> 方法沒有對等的標準函式。  
  
 標準函式 (亦稱為彙總標準函式) 可直接叫用，它們會執行值集的計算，並傳回單一值。 呼叫的其他標準函式則做為 LINQ to Entities 查詢的一部份。 若要直接呼叫彙總函式，您必須將 <xref:System.Data.Objects.ObjectQuery%601> 傳遞至函式。 如需詳細資訊，請參閱下列第二個範例。  
  
 您可以在 LINQ to Entities 查詢中，使用 Common Language Runtime (CLR) 方法呼叫部分標準函式。 如需對應至標準函式的 CLR 方法清單, 請參閱[標準函數對應的 Clr 方法](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)。  
  
## <a name="example"></a>範例  
 下列範例使用[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)。 範例執行 LINQ to Entities 查詢，使用 <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> 方法，傳回 `SellEndDate` 和 `SellStartDate` 之間的差距小於 365 天的所有產品：  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>範例  
 下列範例使用[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)。 範例直接呼叫彙總 <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> 方法，以傳回 `SalesOrderHeader` 小計的標準差。 請注意，<xref:System.Data.Objects.ObjectQuery%601> 已傳遞至函式，函式允許其接受呼叫時，不必成為 LINQ to Entities 查詢的一部份。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [在 LINQ to Entities 查詢中呼叫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
