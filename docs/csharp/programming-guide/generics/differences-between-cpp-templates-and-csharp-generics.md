---
title: C++ 樣板和 C# 泛型之間的差異 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 1bf3eb97d633322f6bd04f8e975ae3fc8ec54329
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651797"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ 樣板和 C# 泛型之間的差異 (C# 程式設計手冊)
C# 泛型和 C++ 範本都是支援參數化型別的語言功能。 不過，這兩個之間有許多差異。 在語法層級，C# 泛型是沒有 C++ 範本複雜性之參數化型別的較簡單方式。 此外，C# 不會嘗試提供 C++ 範本所提供的所有功能。 在實作層級，主要差異是在執行階段執行 C# 泛型型別替代，因而保留具現化物件的泛型型別資訊。 如需詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。  
  
 下列是 C# 泛型與 C++ 範本之間的主要差異：  
  
-   C# 泛型所提供的彈性量與 C++ 範本不同。 例如，雖然它可以呼叫使用者定義運算子，但是無法在 C# 泛型類別中呼叫算術運算子。  
  
-   C# 不允許非類型範本參數，例如 `template C<int i> {}`。  
  
-   C# 不支援明確特製化，即特定類型之範本的自訂實作。  
  
-   C# 不支援部分特製化：類型引數子集的自訂實作。  
  
-   C# 不允許使用型別參數作為泛型型別的基底類別。  
  
-   C# 不允許型別參數具有預設類型。  
  
-   在 C# 中，雖然可以使用建構的類型作為泛型，但是泛型型別參數本身不能是泛型。 C++ 確實允許範本參數。  
  
-   C++ 允許不適用於範本中所有型別參數的程式碼，接著檢查用作型別參數的特定類型。 C# 需要撰寫類別中的程式碼，因此，將會使用符合條件約束的任何類型。 例如，在 C++ 中，可以撰寫在型別參數的物件上使用算術運算子 `+` 和 `-` 的函式，這樣會在使用不支援這些運算子的類型來具現化範本時產生錯誤。 C# 不允許這項作業；允許的唯一語言建構是可從條件約束推算的語言建構。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [範本](/cpp/cpp/templates-cpp)
