---
title: do (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a>do (C# 參考)
`do` 陳述式會重複執行陳述式或陳述式區塊，直到指定的運算式評估為 `false` 為止。 迴圈的主體必須括在大括弧 `{}` 中，除非它的構成是單一陳述式。 在此情況下，大括弧為選擇性。  
  
## <a name="example"></a>範例  
 在下例中，只要變數 `x` 小於 5，`do-while` 迴圈陳述式就會一直執行。  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 不同於 [while](../../../csharp/language-reference/keywords/while.md) 陳述式，條件運算式在評估之前只會執行一次 `do-while` 迴圈。  
  
 您可以使用 [break](../../../csharp/language-reference/keywords/break.md) 陳述式在 `do-while` 區塊的任一點中斷迴圈。 您可以使用 [continue](../../../csharp/language-reference/keywords/continue.md) 陳述式直接逐步執行 `while` 運算式評估陳述式。 如果 `while` 運算式評估為 true，就繼續執行迴圈中的第一個陳述式。 如果運算式評估為 false，就繼續執行 `do-while` 迴圈後面的第一個陳述式。  
  
 [goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式也可以結束 `do-while` 迴圈。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [do-while 陳述式 (C++)](/cpp/cpp/do-while-statement-cpp)  
 [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md)
