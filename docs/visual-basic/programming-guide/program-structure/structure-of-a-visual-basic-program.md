---
title: Visual Basic 程式的結構
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 42e366a844f9c5e80a8f617bf73dfd869608540d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295766"
---
# <a name="structure-of-a-visual-basic-program"></a>Visual Basic 程式的結構
從標準建置組塊，已建立 Visual Basic 程式。 A*解決方案*可以包含一或多個專案。 A*專案*又可以包含一或多個組件。 每個*組件*編譯一或多個原始程式檔。 A*原始程式檔*提供定義和實作的類別、 結構、 模組和介面，最後會包含所有的程式碼。  
  
 Visual Basic 程式的這些建置組塊的相關資訊，請參閱[方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)並[.NET 組件](../../../standard/assembly/index.md)。  
  
## <a name="file-level-programming-elements"></a>檔案層級的程式設計項目  
 當您啟動專案或檔案，並開啟程式碼編輯器中時，您會看到一些程式碼已經位於正確位置，以及正確的順序。 您撰寫任何程式碼應該遵循下列順序：  
  
1. `Option` 陳述式  
  
2. `Imports` 陳述式  
  
3. `Namespace` 陳述式和命名空間層級項目  
  
 如果您以不同方式輸入陳述式，會導致編譯錯誤。  
  
 程式也可以包含條件式編譯陳述式。 您可以顛倒這些原始程式檔之間的上述順序陳述式。  
  
### <a name="option-statements"></a>選項陳述式  
 `Option` 陳述式會建立後續的程式碼，協助避免語法和邏輯錯誤的基本規則。 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)可確保所有變數宣告而且拼字正確，以減少偵錯的時間。 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)可協助您減少可能會發生，當您使用不同的資料型別的變數之間的邏輯錯誤和資料遺失。 [Option 比較陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)指定方法的字串會互相比較，是根據其`Binary`或`Text`值。  
  
### <a name="imports-statements"></a>Imports 陳述式  
 您可以包含[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)匯入您的專案以外定義的名稱。 `Imports`陳述式可讓您的程式碼，來參考類別和其他類型定義中匯入的命名空間，而不必加以限定。 您可以使用多個`Imports`適當的陳述式。 如需詳細資訊，請參閱 <<c0> [ 參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)。  
  
### <a name="namespace-statements"></a>Namespace 陳述式  
 命名空間可協助您組織及分類以方便分組，並存取您的程式設計項目。 您使用[命名空間陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)分類中特定的命名空間的下列陳述式。 如需詳細資訊，請參閱 [Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
### <a name="conditional-compilation-statements"></a>條件式編譯陳述式  
 條件式編譯陳述式可以出現在原始程式檔的幾乎任何地方。 它們會造成您的程式碼来包含或排除在編譯時期，根據特定條件的組件。 您也可以使用它們進行偵錯您的應用程式，因為在偵錯模式只會執行的條件程式碼。 如需詳細資訊，請參閱 <<c0> [ 條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)。  
  
## <a name="namespace-level-programming-elements"></a>命名空間層級的程式設計項目  
 類別、 結構和模組包含原始程式檔中的所有程式碼。 它們*命名空間層級*項目，可以出現在命名空間或在來源檔案層級。 它們會保存所有其他程式設計項目的宣告。 介面，可定義項目簽章，但不提供任何實作，也會出現在模組層級。 如需有關模組層級元素的詳細資訊，請參閱下列各項：  
  
-   [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 在命名空間層級的資料元素是列舉和委派。  
  
## <a name="module-level-programming-elements"></a>模組層級的程式設計項目  
 程序、 運算子、 屬性和事件是唯一的程式設計項目，可保存可執行程式碼 （陳述式會在執行階段中執行的動作）。 它們*模組層級*的程式項目。 如需有關程序層級元素的詳細資訊，請參閱下列各項：  
  
-   [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 在模組層級的資料元素是變數、 常數、 列舉和委派。  
  
## <a name="procedure-level-programming-elements"></a>程序層級的程式設計項目  
 大部分的內容*程序層級*項目是構成您程式的執行階段程式碼的可執行陳述式。 所有的可執行程式碼必須在某個程序 (`Function`， `Sub`， `Operator`， `Get`， `Set`， `AddHandler`， `RemoveHandler`， `RaiseEvent`)。 如需詳細資訊，請參閱[陳述式](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
 在程序層級的資料元素僅限於本機變數和常數。  
  
## <a name="the-main-procedure"></a>在主要程序  
 `Main`程序是已載入您的應用程式時執行的第一個程式碼。 `Main` 可作為起點，並為您的應用程式的整體控制。 有四個不同的`Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 此程序的最常見的各種不同的是`Sub Main()`。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的 Main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 Main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Visual Basic 的限制](../../../visual-basic/programming-guide/program-structure/limitations.md)
