---
title: "如何：呼叫資料庫函式"
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
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b442e1ca096b100e6d7c22303f8c5bcfa49f79d2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-database-functions"></a>如何：呼叫資料庫函式
<xref:System.Data.Objects.SqlClient.SqlFunctions> 類別包含公開 SQL Server 函式以用於 LINQ to Entities 查詢的方法。 使用 LINQ to Entities 中的 <xref:System.Data.Objects.SqlClient.SqlFunctions> 方法時，對應的資料庫函式會在資料庫中執行。  
  
> [!NOTE]
>  可直接叫用的資料庫函式，會執行值集的計算，然後傳回單一值 (亦稱為彙總資料庫函式)。 呼叫的其他標準函式則做為 LINQ to Entities 查詢的一部份。 若要直接呼叫彙總函式，您必須將 <xref:System.Data.Objects.ObjectQuery%601> 傳遞至函式。 如需詳細資訊，請參閱下列第二個範例。  
  
> [!NOTE]
>  <xref:System.Data.Objects.SqlClient.SqlFunctions> 類別中的方法專屬於 SQL Server 函式。 公開資料庫函式的類似類別可透過其他提供者提供。  
  
## <a name="example"></a>範例  
 下列範例會使用[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)。 範例執行 LINQ to Entities 查詢時，會使用 <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> 方法，傳回姓氏以 "Si" 為開頭的所有連絡人：  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>範例  
 下列範例會使用[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)。 範例直接呼叫彙總 <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> 方法。 請注意，<xref:System.Data.Objects.ObjectQuery%601> 已傳遞至函式，函式允許其接受呼叫時，不必成為 LINQ to Entities 查詢的一部份。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>請參閱  
 [在 LINQ to Entities 查詢中呼叫函式](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
