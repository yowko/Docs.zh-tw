---
title: "如何：串連多個字串 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b191a61258a496115a4d7045046f9b4a2dbee58c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>如何：串連多個字串 (C# 程式設計手冊)
「串連」是將一個字串附加至另一個字串結尾的程序。 當您使用 `+` 運算子串連字串常值或字串常數時，編譯器會建立單一字串。 不會發生執行階段串連。 不過，字串變數只會在執行階段串連。 這種情況下，您應該了解各種方法的效能含意。  
  
## <a name="example"></a>範例  
 下例示範如何將長字串常值分割成較小的字串，以改善原始程式碼的可讀性。 這些組件在編譯時期會串連成單一字串。 不論涉及多少字串，都沒有執行階段效能成本。  
  
 [!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>範例  
 若要串連字串變數，您可以使用 `+` 或 `+=` 運算子，或使用 <xref:System.String.Concat%2A?displayProperty=fullName>、<xref:System.String.Format%2A?displayProperty=fullName> 或 <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> 方法。 `+` 運算子簡單易用，且容易建立直覺化程式碼。 即使一個陳述式使用數個 + 運算子，字串內容也只會複製一次。 但若是多次重複這項作業，例如在迴圈中，可能會造成效率問題。 例如，請注意下列程式碼：  
  
 [!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  在字串串連作業中，C# 編譯器會將 null 字串視同空字串，但不會轉換原始的 null 字串值。  
  
 如果不串連大量的字串 (例如，在迴圈中)，這段程式碼的效能成本可能就不那麼明顯。 <xref:System.String.Concat%2A?displayProperty=fullName> 和 <xref:System.String.Format%2A?displayProperty=fullName> 方法也同樣如此。  
  
 不過，當效能很重要時，您應該一律使用 <xref:System.Text.StringBuilder> 類別來串連字串。 下列程式碼會使用 <xref:System.Text.StringBuilder> 類別的 <xref:System.Text.StringBuilder.Append%2A> 方法來串連字串，沒有 `+` 運算子的鏈結效果。  
  
 [!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String>   
 <xref:System.Text.StringBuilder>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)

