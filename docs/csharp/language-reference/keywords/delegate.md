---
title: "delegate (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a>delegate (C# 參考)
委派類型的宣告類似方法簽章。 它具有傳回值以及任意類型之任何數目的參數：  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 `delegate` 是可用來封裝具名或匿名方法的參考型別。 委派類似 C++ 中的函式指標，但委派是型別安全而且安全的。 如需委派的應用程式，請參閱[委派](../../../csharp/programming-guide/delegates/index.md)和[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。  
  
## <a name="remarks"></a>備註  
 委派是[事件](../../../csharp/programming-guide/events/index.md)的基礎。  
  
 委派的具現化方式是將它與具名或匿名方法建立關聯。 如需詳細資訊，請參閱[具名方法](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)和[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。  
  
 委派必須使用具有相容傳回型別和輸入參數的方法或 Lambda 運算式進行具現化。 如需方法簽章中所允許變異程度的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) (委派中的變異數)。 若與匿名方法搭配使用，則會一起宣告要與它建立關聯的委派和程式碼。 本節討論兩種具現化委派的方式。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)  
 [委派](../../../csharp/programming-guide/delegates/index.md)  
 [事件](../../../csharp/programming-guide/events/index.md)  
 [具名方法委派與匿名方法委派](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
