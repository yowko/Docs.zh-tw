---
title: break (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a>break (C# 參考)
`break` 陳述式會終止其所在的最接近封閉式迴圈或 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式。 控制權會轉移到已終止陳述式之後的陳述式 (如果有的話)。  
  
## <a name="example"></a>範例  
 在此範例中，條件式陳述式包含假設從 1 計算到 100 的計數器；不過，`break` 陳述式會在計算 4 次之後終止迴圈。  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a>範例  
 在此範例中，`break` 陳述式是用來破壞內部巢狀迴圈，並將控制權返回外部迴圈。  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a>範例  
 這個範例示範如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `break`。  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 如果您已輸入 `4`，則輸出會是︰  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [switch](../../../csharp/language-reference/keywords/switch.md)  
 [跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)  
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)
