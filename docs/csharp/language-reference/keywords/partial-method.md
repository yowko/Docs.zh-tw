---
title: "partial (方法) (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialmethod_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
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
ms.openlocfilehash: b6f8ecca01ebf681c906b73abefc94e9e45b8700
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="partial-method-c-reference"></a>partial (方法) (C# 參考)
部分方法會在部分型別的某一部分中定義其簽章，並在類型的另一部分中定義其實作。 部分方法可讓類別設計工具提供方法攔截程序，類似於事件處理常式，開發人員可以決定是否實作。 如果開發人員未提供實作，編譯器會在編譯時期移除簽章。 下列條件適用於部分方法：  
  
-   部分型別的兩個部分中的簽章必須相符。  
  
-   此方法必須傳回 void。  
  
-   不允許存取修飾詞。 部分方法都是隱含私用。  
  
 下列範例顯示部分類別之兩個部分中定義的部分方法：  
  
 [!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 如需詳細資訊，請參閱[部分類別與方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [partial (型別)](../../../csharp/language-reference/keywords/partial-type.md)

