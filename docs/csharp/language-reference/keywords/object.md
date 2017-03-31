---
title: "object (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
dev_langs:
- CSharp
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
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
ms.openlocfilehash: cf1ec249c928f4bc23827ef0b831a8a64659ab8c
ms.lasthandoff: 03/13/2017

---
# <a name="object-c-reference"></a>object (C# 參考)
`object` 型別在 .NET Framework 中是 <xref:System.Object> 的別名。 在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。 您可以將任何型別的值指派給 `object` 型別的變數。 當實值型別的變數轉換成物件時，即稱之為 *Boxed*。 當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。 如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。  
  
## <a name="example"></a>範例  
 以下範例示範 `object` 型別的變數如何接受任何資料類型的值，以及 `object` 型別的變數如何從 .NET Framework 對 <xref:System.Object> 使用方法。  
  
 [!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)   
 [實值型別](../../../csharp/language-reference/keywords/value-types.md)
