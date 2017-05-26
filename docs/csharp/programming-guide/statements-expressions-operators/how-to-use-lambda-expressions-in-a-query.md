---
title: "如何：在查詢中使用 Lambda 運算式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7bfc46015b0d4603c4d63478e804f862c0c65b68
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>如何：在查詢中使用 Lambda 運算式 (C# 程式設計手冊)
您不會在查詢語法中直接使用 Lambda 運算式，而是在方法呼叫中使用它們，因此查詢運算式可以包含方法呼叫。 事實上，某些查詢作業只能以方法語法來表示。 如需查詢語法與方法語法之間差異的詳細資訊，請參閱 [LINQ 中的查詢語法及方法語法](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何透過 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 標準查詢運算子，在以方法為基礎的查詢中使用 Lambda 運算式。 請注意，此範例中的 <xref:System.Linq.Enumerable.Where%2A> 方法具有委派類型 <xref:System.Func%601> 的輸入參數，而且該委派會接受整數作為輸入並傳回布林值。 Lambda 運算式可轉換成該委派。 如果這是使用 <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName> 方法的 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)] 查詢，參數類型就會是 `Expression<Func\<int,bool>>`，但 Lambda 運算式看起來會完全相同。 如需運算式類型的詳細資訊，請參閱 <xref:System.Linq.Expressions.Expression?displayProperty=fullName>。  
  
 [!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何在查詢運算式的方法呼叫中使用 Lambda 運算式。 因為無法使用查詢語法來叫用 <xref:System.Linq.Enumerable.Sum%2A> 標準查詢運算子，所以需要此 Lambda。  
  
 此查詢會先根據學生的年級 (已定義於 `GradeLevel` 列舉) 來進行分組。 接著會針對每一組加總計算每個學生的總分數。 這需要兩個 `Sum` 運算。 內部的 `Sum` 會計算每個學生的總分數，而外部的 `Sum` 會不斷執行，以加總該群組中所有學生的總分數。  
  
 [!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將該方法複製並貼到[如何︰查詢物件集合](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)中所提供的 `StudentClass`，然後從 `Main` 方法進行呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [運算式樹狀結構](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
