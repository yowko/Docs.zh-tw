---
title: 制定投影
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: d8215a016face76b8a258d694a36657be327b5e0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="formulate-projections"></a>制定投影
下列範例會顯示如何`select`C# 中的陳述式和`Select`在 Visual Basic 中的陳述式可以結合其他功能，以構成查詢投影。  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 以傳回的連絡人名稱序列`Customers`。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*要傳回的連絡人名稱序列和電話號碼`Customers`。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*傳回一連串的名稱，並為員工電話號碼。 `FirstName`和`LastName`欄位會合併成單一欄位 (`Name`)，而`HomePhone`欄位重新命名為`Phone`中所產生的順序。  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*以傳回所有序列`ProductID`s 和名為的導出的值`HalfPrice`。 此值設為 `UnitPrice` 除以 2。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*條件陳述式*傳回一連串的產品名稱和產品可用性。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>範例  
 下列範例會使用 Visual Basic`Select`子句 (`select`子句在 C# 中的) 和*已知型別*(Name)，傳回員工的名稱的序列。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`和`Where`在 Visual Basic 中 (`select`和`where`C# 中) 來傳回*篩選順序*位於倫敦的客戶的連絡人名稱。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Select`在 Visual Basic 中的子句 (`select`子句在 C# 中的) 和*匿名型別*傳回*形狀子集*客戶相關的資料。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>範例  
 下列範例使用巢狀查詢，傳回下列結果：  
  
-   所有訂單與其對應 `OrderID` 的序列。  
  
-   訂單中有折扣之項目的序列。  
  
-   不包含運送成本時所節省的金額。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
