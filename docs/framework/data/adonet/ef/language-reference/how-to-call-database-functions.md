---
title: 作法：呼叫資料庫函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: dd440be3f73eb2f02a269a8cad29f0fe30920836
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936030"
---
# <a name="how-to-call-database-functions"></a>HOW TO：呼叫資料庫函式
<xref:System.Data.Objects.SqlClient.SqlFunctions> 類別包含公開 SQL Server 函式以用於 LINQ to Entities 查詢的方法。 使用 LINQ to Entities 中的 <xref:System.Data.Objects.SqlClient.SqlFunctions> 方法時，對應的資料庫函式會在資料庫中執行。  
  
> [!NOTE]
> 可直接叫用的資料庫函式，會執行值集的計算，然後傳回單一值 (亦稱為彙總資料庫函式)。 呼叫的其他標準函式則做為 LINQ to Entities 查詢的一部份。 若要直接呼叫彙總函式，您必須將 <xref:System.Data.Objects.ObjectQuery%601> 傳遞至函式。 如需詳細資訊，請參閱下列第二個範例。  
  
> [!NOTE]
> <xref:System.Data.Objects.SqlClient.SqlFunctions> 類別中的方法專屬於 SQL Server 函式。 公開資料庫函式的類似類別可透過其他提供者提供。  
  
## <a name="example"></a>範例  
 下列範例使用[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)。 範例執行 LINQ to Entities 查詢時，會使用 <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> 方法，傳回姓氏以 "Si" 為開頭的所有連絡人：  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>範例  
 下列範例使用[AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)。 範例直接呼叫彙總 <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> 方法。 請注意，<xref:System.Data.Objects.ObjectQuery%601> 已傳遞至函式，函式允許其接受呼叫時，不必成為 LINQ to Entities 查詢的一部份。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [在 LINQ to Entities 查詢中呼叫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
