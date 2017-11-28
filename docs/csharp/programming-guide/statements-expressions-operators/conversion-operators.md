---
title: "轉換運算子 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5277c1160c604ee56ff575df5bd603e115588d21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-operators-c-programming-guide"></a>轉換運算子 (C# 程式設計手冊)
C# 可讓程式設計人員宣告類別或結構轉換，使類別或結構能夠與其他類別、結構或基本類型相互轉換。 轉換的定義方式類似運算子，並會以轉換的目標類型命名。 在引數所要轉換的目標類型或轉換的結果類型中，必須有一個是包含類型，但不能兩者都是。  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>轉換運算子概觀  
 轉換運算子具有下列屬性：  
  
-   宣告為 `implicit` 的轉換會在必要時自動發生。  
  
-   宣告為 `explicit` 的轉換需要呼叫轉換。  
  
-   所有轉換都必須宣告為 `static`。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [轉換和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Convert>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 中鏈結的使用者定義明確轉換](http://go.microsoft.com/fwlink/?LinkId=112384)
