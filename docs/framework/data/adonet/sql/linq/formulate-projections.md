---
title: 制定投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194397"
---
# <a name="formulate-projections"></a>制定投影

下列範例示範 `select` c # 中的語句和 `Select` Visual Basic 中的語句如何與其他功能結合，以構成查詢投影。  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` c # ) 的 Visual Basic (子句中使用子句 `select` ，以傳回的連絡人名稱序列 `Customers` 。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名型別* 會傳回的連絡人名稱和電話號碼序列 `Customers` 。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名* 型別，以傳回員工的名稱和電話號碼序列。 `FirstName`和 `LastName` 欄位會合並成單一欄位 (`Name`) ，而且 `HomePhone` 欄位會 `Phone` 在產生的序列中重新命名為。  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名* 型別會傳回所有 s 的序列 `ProductID` 和名為的計算值 `HalfPrice` 。 此值設為 `UnitPrice` 除以 2。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` c # ) 中使用 Visual Basic (子句中的子句 `select` ，並使用 *條件陳述式* 來傳回產品名稱和產品可用性的序列。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>範例  

 下列範例會 `Select` `select` 在 c # 中使用 Visual Basic 子句 (子句 ) 以及 *已知的類型* (名稱) ，以傳回員工名稱的序列。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` `Where` Visual Basic (`select` 和 `where` c # ) 中使用和，以針對位於倫敦的客戶傳回已篩選的連絡人名稱 *序列* 。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>範例  

 下列範例會在 `Select` c # 中使用 Visual Basic (子句中的子句 `select` ) 和 *匿名* 型別，以傳回客戶相關資料的 *成形子集* 。  
  
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
