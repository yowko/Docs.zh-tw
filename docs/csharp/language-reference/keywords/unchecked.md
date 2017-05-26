---
title: "unchecked (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
dev_langs:
- CSharp
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
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
ms.openlocfilehash: 8110e27fea712e916cf8550d22399a6532a6f95e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="unchecked-c-reference"></a>unchecked (C# 參考)
`unchecked` 關鍵字是用來抑制整數類型算術運算和轉換的溢位檢查。  
  
 在未檢查的內容中，如果運算式產生不在目的類型範圍內的值，則不會標示溢位。 例如，因為是在 `unchecked` 區塊或運算式中執行下列範例中的計算，所以會忽略整數結果太大的事實，而且 `int1` 會獲指派 -2,147,483,639 值。  
  
 [!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 如果移除 `unchecked` 環境，則會發生編譯錯誤。 因為運算式的所有項目都是常數，所以會在編譯時期偵測到溢位。  
  
 預設不會在編譯時期和執行階段檢查包含非常數項目的運算式。 如需啟用已檢查環境的資訊，請參閱 [checked](../../../csharp/language-reference/keywords/checked.md)。  
  
 因為檢查溢位需要一些時間，所以在沒有溢位危險的情況下使用未檢查的程式碼可能會改善效能。 不過，如果可能會發生溢位，則應該使用已檢查過的環境。  
  
## <a name="example"></a>範例  
 這個範例示範如何使用 `unchecked` 關鍵字。  
  
 [!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [checked](../../../csharp/language-reference/keywords/checked.md)
