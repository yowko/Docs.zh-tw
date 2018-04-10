---
title: object (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0fcced75d3a86fd700e642e48b7e325e554cae53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-c-reference"></a>object (C# 參考)
`object` 類型是 <xref:System.Object> 在 .NET Framework 中的別名。 在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。 您可以將任何型別的值指派給 `object` 型別的變數。 當實值型別的變數轉換成物件時，即稱之為 *Boxed*。 當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。 如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。  
  
## <a name="example"></a>範例  
 以下範例示範 `object` 類型的變數如何接受任何資料類型的值，以及 `object` 類型的變數如何從 .NET Framework 對 <xref:System.Object> 使用方法。  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [參考型別](../../../csharp/language-reference/keywords/reference-types.md)  
 [實值型別](../../../csharp/language-reference/keywords/value-types.md)
