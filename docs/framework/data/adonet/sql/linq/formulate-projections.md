---
title: 制定投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793825"
---
# <a name="formulate-projections"></a>制定投影
下列範例會示範如何將`select` Visual Basic 中C#的`Select`語句與其他功能結合，以形成查詢投影。  
  
## <a name="example"></a>範例  
 下列範例會在中`Select` C#使用 Visual Basic （ `Customers` `select`子句）中的子句，以傳回的連絡人名稱序列。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>範例  
 下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名*型別中使用子句，以傳回的連絡人名稱和電話號碼`Customers`序列。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>範例  
 下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名型別*中使用子句，以傳回員工的名稱和電話號碼序列。 `Phone` `HomePhone` `Name`和欄位會合並成單一欄位（），而欄位會在產生的序列中重新命名為。 `LastName` `FirstName`  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>範例  
 下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名*型別中使用子句，以傳回所有`ProductID`的序列和名為`HalfPrice`的計算值。 此值設為 `UnitPrice` 除以 2。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>範例  
 下列範例會在的`Select` Visual Basic （`select`子句C#）和*條件陳述式*中使用子句，以傳回產品名稱和產品可用性的序列。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>範例  
 下列範例`Select`會使用 Visual Basic 子句（`select`中C#的子句）和*已知型*別（名稱）來傳回員工名稱的序列。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>範例  
 下列範例會在`Select` Visual Basic `Where`中使用和`select` （ `where`在C#中為），以針對倫敦的客戶傳回已篩選的連絡人名稱*序列*。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>範例  
 下列範例會在的`Select` Visual Basic （`select`子句C#）和*匿名*型別中使用子句，以傳回有關客戶資料的*形狀子集*。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>範例  
 下列範例使用巢狀查詢，傳回下列結果：  
  
- 所有訂單與其對應 `OrderID` 的序列。  
  
- 訂單中有折扣之項目的序列。  
  
- 不包含運送成本時所節省的金額。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>另請參閱

- [查詢範例](query-examples.md)
