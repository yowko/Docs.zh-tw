---
title: "泛型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4899b3604343925e7e4e0535929d041b1a1f1081
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="generics-c-programming-guide"></a>泛型 (C# 程式設計手冊)
泛型是在 C# 語言和 Common Language Runtime (CLR) 的 2.0 版中新增的功能。 泛型將型別參數的概念引進 .NET Framework 中，使得類別和方法在設計時，可以先行擱置一或多個類型的規格，直到用戶端程式碼對類別或方法進行宣告或具現化時再行處理。 例如，您可以使用泛型型別參數 T，撰寫一個類別供其他用戶端程式碼使用，而不會在執行階段產生轉換或 boxing 作業的成本或風險，如下所示：  
  
 [!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>泛型概觀  
  
-   使用泛型型別以最佳化程式碼重複使用、型別安全和效能。  
  
-   泛型的最常見用法是建立集合類別。  
  
-   .NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。 您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。  
  
-   您可以建立自己的泛型介面、類別、方法、事件和委派。  
  
-   泛型類別可限制為允許存取特定資料類型上的方法。  
  
-   泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [泛型的優點](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [泛型型別參數](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [泛型介面](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [default 關鍵字](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md)  
  
-   [C++ 範本和 C# 泛型之間的差異](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [泛型和反映](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [.NET Framework 類別庫中的泛型](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 如需詳細資訊，請參閱＜[C# 語言規格](../../../csharp/language-reference/language-specification/index.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic>   
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [類型](../../../csharp/programming-guide/types/index.md)   
 [\<類型參數>](../../../csharp/programming-guide/xmldoc/typeparam.md)   
 [\<類型參數參考>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

