---
title: goto (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 2dd70a30b885dcdae9637b02e8c34ac39f4879fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="goto-c-reference"></a>goto (C# 參考)
`goto` 陳述式會將程式控制權直接轉移到標記陳述式。  
  
 `goto` 的一個常見用法是將控制權轉移到特定的切換案例標籤，或 `switch` 陳述式中的預設標籤。  
  
 `goto` 陳述式也適用於跳出深度巢狀的迴圈。  
  
## <a name="example"></a>範例  
 下列範例示範如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `goto`。  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `goto` 跳出巢狀迴圈。  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [goto 陳述式](/cpp/cpp/goto-statement-cpp)  
 [跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)
