---
title: unchecked (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: d7a48950b7158be3cd589c20fbfe0661f3c9c5af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="unchecked-c-reference"></a>unchecked (C# 參考)
`unchecked` 關鍵字是用來抑制整數類型算術運算和轉換的溢位檢查。  
  
 在未檢查的內容中，如果運算式產生不在目的類型範圍內的值，則不會標示溢位。 例如，因為是在 `unchecked` 區塊或運算式中執行下列範例中的計算，所以會忽略整數結果太大的事實，而且 `int1` 會獲指派 -2,147,483,639 值。  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 如果移除 `unchecked` 環境，則會發生編譯錯誤。 因為運算式的所有項目都是常數，所以會在編譯時期偵測到溢位。  
  
 預設不會在編譯時期和執行階段檢查包含非常數項目的運算式。 如需啟用已檢查環境的資訊，請參閱 [checked](../../../csharp/language-reference/keywords/checked.md)。  
  
 因為檢查溢位需要一些時間，所以在沒有溢位危險的情況下使用未檢查的程式碼可能會改善效能。 不過，如果可能會發生溢位，則應該使用已檢查過的環境。  
  
## <a name="example"></a>範例  
 這個範例示範如何使用 `unchecked` 關鍵字。  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [checked](../../../csharp/language-reference/keywords/checked.md)
