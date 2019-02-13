---
title: .NET 效能秘訣
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2969551bef279e6b13d2b08ff7f0e4711a80794
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219239"
---
# <a name="net-performance-tips"></a>.NET 效能秘訣
「效能」這個詞一般指的是程式的執行速度。 您有時可以遵循原始程式碼中的特定基本規則來增加執行速度。 在某些程式中，請務必仔細檢查程式碼，並使用程式碼剖析工具，確定以最快速度執行。 在其他程式中，您不需要執行這類最佳化，因為程式碼會以撰寫時的可接受速度快速執行。 本文列出效能可能會降低的一些常見區域和其改善祕訣，以及其他效能主題的連結。 如需效能規劃和測量的詳細資訊，請參閱[效能](../../../docs/framework/performance/index.md)。  
  
## <a name="boxing-and-unboxing"></a>Boxing 和 Unboxing  
 如果必須對實值型別進行 Boxing 處理多次，則最好避免使用實值型別，例如，在 <xref:System.Collections.ArrayList?displayProperty=nameWithType> 這類非泛型集合類別中。 您可以使用 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 這類泛型集合，避免對實值型別進行 Boxing 處理。 Boxing 和 Unboxing 是會耗費大量運算資源的處理序。 對實值型別進行 Boxing 處理時，必須建立全新的物件。 這所需的時間最多是簡單參考指派的 20 倍。 Unboxing 處理時，轉換處理序可能需要指派的四倍時間。 如需詳細資訊，請參閱 [Boxing 和 Unboxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md)。  
  
## <a name="strings"></a>字串  
 當您串連大量字串變數時 (例如在緊密迴圈中)，請使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType>，而非 C# [+ 運算子](~/docs/csharp/language-reference/operators/addition-operator.md)或 Visual Basic [串連運算子](~/docs/visual-basic/language-reference/operators/concatenation-operators.md)。 如需詳細資訊，請參閱[如何：多個字串串連](../../csharp/how-to/concatenate-multiple-strings.md)並[串連運算子，在 Visual Basic 中的](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)。  
  
## <a name="destructors"></a>解構函式  
 不應該使用空的解構函式。 類別包含解構函式時，會在 Finalize 佇列中建立一個項目。 呼叫解構函式時，會叫用記憶體回收行程來處理佇列。 如果解構函式是空的，則這只會導致效能降低。 如需詳細資訊，請參閱 <<c0> [ 解構函式](~/docs/csharp/programming-guide/classes-and-structs/destructors.md)和[物件存留期：如何建立和終結物件](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
## <a name="other-resources"></a>其他資源  
  
-   [更快速撰寫 Managed 程式碼：知道事項的成本](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [撰寫高效能 Managed 應用程式：入門](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Garbage Collector Basics and Performance Hints](https://go.microsoft.com/fwlink/?LinkId=99296) (記憶體回收行程基本概念和效能提示)  
  
-   [Performance Tips and Tricks in .NET Applications](https://go.microsoft.com/fwlink/?LinkId=99297) (.NET 應用程式中的效能祕訣和訣竅)  

-   [Rico Mariani's Performance Tidbits](https://go.microsoft.com/fwlink/?LinkId=115679) (Rico Mariani 的效能花絮)  

-   [Vance Morrison 的部落格](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>另請參閱
- [效能](../../../docs/framework/performance/index.md)
- [Visual Basic 程式設計手冊](../../visual-basic/programming-guide/index.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
