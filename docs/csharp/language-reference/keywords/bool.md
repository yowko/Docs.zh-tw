---
title: "bool (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
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
ms.openlocfilehash: ef8cc9a0584829eeed06e7fc3c2227f0683ef413
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="bool-c-reference"></a>bool (C# 參考)
`bool` 關鍵字是 <xref:System.Boolean?displayProperty=fullName> 的別名。 它是用來宣告可儲存布林值 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的變數。  
  
> [!NOTE]
>  如果您需要也可以有 `null` 值的布林值變數，請使用 `bool?`。 如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。  
  
## <a name="literals"></a>常值  
 您可以將布林值指派給 `bool` 變數。 您也可以將評估為 `bool` 的運算式指派給 `bool` 變數。  
  
 [!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 `bool` 變數的預設值是 `false`。 `bool?` 變數的預設值是 `null`。  
  
## <a name="conversions"></a>轉換  
 在 C++ 中，`bool` 類型的值可以轉換為 `int` 類型的值；換句話說，`false` 相當於零，`true` 則相當於非零值。 在 C# 中，於 `bool` 類型與其他類型之間不會進行轉換。 例如，下列 `if` 陳述式在 C# 中無效：  
  
 [!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 若要測試 `int` 類型的變數，您必須明確地比較它與值 (例如零)，如下所示：  
  
 [!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>範例  
 在此範例中，您使用鍵盤輸入字元，而程式會檢查輸入字元是否為字母。 如果是字母，則會檢查是小寫還是大寫。 會使用 <xref:System.Char.IsLetter%2A> 和 <xref:System.Char.IsLower%2A> 來執行這些檢查，而這兩者會傳回 `bool` 類型：  
  
 [!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
