---
title: "while (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 744980f2dd55806062901d874a3137f5936e0888
ms.lasthandoff: 03/13/2017

---
# <a name="while-c-reference"></a>while (C# 參考)
`while` 陳述式會執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。  
  
## <a name="example"></a>範例  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>範例  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>範例  
 `while` 運算式的測試是在每次執行迴圈之前發生，因此 `while` 迴圈會執行零次或多次。 這與 [do](../../../csharp/language-reference/keywords/do.md) 迴圈不同，此迴圈會執行一次或多次。  
  
 [break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式將控制權轉移到迴圈外部時，即可終止 `while` 迴圈。 若要將控制權傳遞給下一個反覆運算，而不結束迴圈，請使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式。 請注意三個先前範例中的輸出差異，根據遞增 `int n` 的位置而定。 在下面的範例中，不會產生任何輸出。  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [while 陳述式 (C++)](https://docs.microsoft.com/cpp/cpp/while-statement-cpp)   
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)
