---
title: HOW TO：在查詢中使用 Lambda 運算式 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 18f8823327719a120888df580779125be5d07b2c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965627"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>HOW TO：在查詢中使用 Lambda 運算式 (C# 程式設計指南)
您不會在查詢語法中直接使用 Lambda 運算式，而是在方法呼叫中使用它們，因此查詢運算式可以包含方法呼叫。 事實上，某些查詢作業只能以方法語法來表示。 如需查詢語法與方法語法之間差異的詳細資訊，請參閱 [LINQ 中的查詢語法及方法語法](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何透過 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 標準查詢運算子，在以方法為基礎的查詢中使用 Lambda 運算式。 請注意，此範例中的 <xref:System.Linq.Enumerable.Where%2A> 方法具有委派類型 <xref:System.Func%601> 的輸入參數，而且該委派會接受整數作為輸入並傳回布林值。 Lambda 運算式可轉換成該委派。 如果這是使用 <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> 方法的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查詢，參數類型就會是 `Expression<Func<int,bool>>`，但 Lambda 運算式看起來會完全相同。 如需運算式類型的詳細資訊，請參閱 <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>。  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>範例  
 下列範例示範如何在查詢運算式的方法呼叫中使用 Lambda 運算式。 因為無法使用查詢語法來叫用 <xref:System.Linq.Enumerable.Sum%2A> 標準查詢運算子，所以需要此 Lambda。  
  
 此查詢會先根據學生的年級 (已定義於 `GradeLevel` 列舉) 來進行分組。 接著會針對每一組加總計算每個學生的總分數。 這需要兩個 `Sum` 運算。 內部的 `Sum` 會計算每個學生的總分數，而外部的 `Sum` 會不斷執行，以加總該群組中所有學生的總分數。  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請複製方法並貼上到下列文件中提供的 `StudentClass` 中：[如何：查詢物件集合](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)，然後從 `Main` 方法呼叫它。  
  
## <a name="see-also"></a>另請參閱

- [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [運算式樹狀結構 (C#)](../concepts/expression-trees/index.md)
