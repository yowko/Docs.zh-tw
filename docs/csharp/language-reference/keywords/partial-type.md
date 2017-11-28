---
title: "partial (類型) (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords: partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5212984cc577ce05fc4697e0d648fb5545528562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="partial-type-c-reference"></a>partial (類型) (C# 參考)
部分型別定義允許將類別、結構或介面定義分割成多個檔案。  
  
 在 File1.cs 中：  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 在 File2.cs 中宣告︰  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a>備註  
 將類別、結構或介面型別分割成數個檔案在處理大型專案，或者處理自動產生的程式碼，例如 [Windows Forms 設計工具](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)提供的程式碼時，會很有用。 部分類別可包含[部分方法](../../../csharp/language-reference/keywords/partial-method.md)。 如需詳細資訊，請參閱[部分類別與方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)
