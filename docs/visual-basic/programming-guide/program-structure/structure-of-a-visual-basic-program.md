---
title: Visual Basic 程式的結構
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: dc6b38d78f02a42c8e7cc2aa964e9f3f74996f44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408760"
---
# <a name="structure-of-a-visual-basic-program"></a>Visual Basic 程式的結構
Visual Basic 程式是由標準的建築組塊所建立。 *解決方案*包含一或多個專案。 *專案*接著可以包含一個或多個元件。 每個元件都是從一或多個原始*程式*檔編譯而來。 *原始*程式檔提供類別、結構、模組和介面的定義和實作為，其最終會包含您的所有程式碼。  
  
 如需有關 Visual Basic 程式的這些構成要素的詳細資訊，請參閱[.net 中](../../../standard/assembly/index.md)的[方案和專案](/visualstudio/ide/solutions-and-projects-in-visual-studio)和元件。  
  
## <a name="file-level-programming-elements"></a>檔案層級的程式設計項目  
 當您啟動專案或檔案，並開啟 [程式碼編輯器] 時，您會看到一些已備妥的程式碼，並以正確的順序顯示。 您撰寫的任何程式碼都應該遵循下列順序：  
  
1. `Option`報表  
  
2. `Imports`報表  
  
3. `Namespace`語句和命名空間層級元素  
  
 如果您以不同的順序輸入語句，可能會導致編譯錯誤。  
  
 程式也可以包含條件式編譯語句。 您可以在來源檔案中，于上述序列的語句之間散置這些檔案。  
  
### <a name="option-statements"></a>Option 語句  
 `Option`語句會建立後續程式碼的基礎規則，協助防止語法和邏輯錯誤。 [Option Explicit 語句](../../language-reference/statements/option-explicit-statement.md)可確保所有變數都已正確宣告和拼寫，以減少調試時間。 [Option Strict 語句](../../language-reference/statements/option-strict-statement.md)有助於將在不同資料類型的變數之間工作時，可能會發生的邏輯錯誤和資料遺失降至最低。 [Option Compare 語句](../../language-reference/statements/option-compare-statement.md)會根據其或值，指定字串相互比較的方式 `Binary` `Text` 。  
  
### <a name="imports-statements"></a>Imports 語句  
 您可以包含[Imports 語句（.Net 命名空間和類型）](../../language-reference/statements/imports-statement-net-namespace-and-type.md) ，以匯入在專案之外定義的名稱。 `Imports`語句可讓您的程式碼參考已匯入之命名空間內定義的類別和其他類型，而不需要限定它們。 您可以視需要使用多個 `Imports` 語句。 如需詳細資訊，請參閱[References 和 Imports 語句](references-and-the-imports-statement.md)。  
  
### <a name="namespace-statements"></a>Namespace 語句  
 命名空間可協助您組織和分類程式設計項目，以方便分組和存取。 您可以使用[Namespace 語句](../../language-reference/statements/namespace-statement.md)來分類特定命名空間內的下列語句。 如需詳細資訊，請參閱 [Visual Basic 中的命名空間](namespaces.md)。  
  
### <a name="conditional-compilation-statements"></a>條件式編譯語句  
 條件式編譯語句幾乎可以出現在原始程式檔中的任何位置。 視特定條件而定，它們會在編譯時期包含或排除程式碼的各個部分。 您也可以使用它們來對應用程式進行錯用，因為條件式程式碼只會在偵測模式中執行。 如需詳細資訊，請參閱[條件式編譯](conditional-compilation.md)。  
  
## <a name="namespace-level-programming-elements"></a>命名空間層級的程式設計項目  
 類別、結構和模組包含來源檔案中的所有程式碼。 它們是*命名空間層級*的元素，可能會出現在命名空間或來源檔案層級。 它們會保存所有其他程式設計項目的宣告。 定義專案簽章但不提供任何執行的介面也會出現在模組層級。 如需模組層級元素的詳細資訊，請參閱下列各項：  
  
- [Class 陳述式](../../language-reference/statements/class-statement.md)  
  
- [Structure 陳述式](../../language-reference/statements/structure-statement.md)  
  
- [Module 陳述式](../../language-reference/statements/module-statement.md)  
  
- [Interface 陳述式](../../language-reference/statements/interface-statement.md)  
  
 命名空間層級的資料元素是列舉和委派。  
  
## <a name="module-level-programming-elements"></a>模組層級的程式設計項目  
 程式、運算子、屬性和事件是唯一可以保存可執行程式碼的程式設計項目（在執行時間執行動作的語句）。 這些是程式的*模組層級*元素。 如需程式層級元素的詳細資訊，請參閱下列各項：  
  
- [Function 陳述式](../../language-reference/statements/function-statement.md)  
  
- [Sub 陳述式](../../language-reference/statements/sub-statement.md)  
  
- [Declare Statement](../../language-reference/statements/declare-statement.md)  
  
- [Operator Statement](../../language-reference/statements/operator-statement.md)  
  
- [Property Statement](../../language-reference/statements/property-statement.md)  
  
- [Event 陳述式](../../language-reference/statements/event-statement.md)  
  
 模組層級的資料元素為變數、常數、列舉和委派。  
  
## <a name="procedure-level-programming-elements"></a>程式層級的程式設計項目  
 程式*層級*專案的大部分內容都是可執行檔語句，這構成了程式的執行時間程式碼。 所有可執行檔程式碼都必須在某個程式中（ `Function` 、 `Sub` 、 `Operator` 、 `Get` 、 `Set` 、、 `AddHandler` `RemoveHandler` 、 `RaiseEvent` ）。 如需詳細資訊，請參閱[陳述式](../language-features/statements.md)。  
  
 程式層級的資料元素僅限於本機變數和常數。  
  
## <a name="the-main-procedure"></a>主要程式  
 `Main`程式是您的應用程式載入時要執行的第一個程式碼。 `Main`作為應用程式的起點和整體控制。 有四種種類 `Main` ：  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 此程式最常見的不同之處是 `Sub Main()` 。 如需詳細資訊，請參閱[Visual Basic 中的 Main](main-procedure.md)程式。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 Main 程序](main-procedure.md)
- [Visual Basic 命名慣例](naming-conventions.md)
- [Visual Basic 的限制](limitations.md)
