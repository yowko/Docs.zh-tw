---
title: "checked (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
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
ms.openlocfilehash: 5826c8e6f99352c730824bb504a168226b9e6600
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="checked-c-reference"></a>checked (C# 參考)
`checked` 關鍵字是用來明確啟用整數型別算術運算和轉換的溢位檢查。  
  
 根據預設，如果運算式產生超出目的地類型範圍的值，則只包含常數值的運算式會導致編譯器錯誤。 如果運算式包含一或多個非常數值，則編譯器偵測不到溢位。 評估下列範例中指派給 `i2` 的運算式不會導致編譯器錯誤。  
  
 [!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 根據預設，不會檢查這些非常數運算式是否在執行階段溢位，而且它們不會引發溢位例外狀況。 先前的範例會顯示 -2,147,483,639 作為兩個正整數的總和。  
  
 可以透過編譯器選項、環境設定或使用 `checked` 關鍵字來啟用溢位檢查。 下列範例示範如何使用 `checked` 運算式或 `checked` 區塊，來偵測先前的總和在執行階段所產生的溢位。 這兩個範例都會引發溢位例外狀況。  
  
 [!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字可以用來防止溢位檢查。  
  
## <a name="example"></a>範例  
 這個範例示範如何使用 `checked`，以在執行階段啟用溢位檢查。  
  
 [!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
