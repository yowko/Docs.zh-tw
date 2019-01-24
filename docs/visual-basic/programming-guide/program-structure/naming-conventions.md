---
title: Visual Basic 命名慣例
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: ebb9d21e32993f2eb035993d32dc3de7d97b49f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672132"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic 命名慣例
當您在 Visual Basic 應用程式中命名的項目時，該名稱的第一個字元必須是英數字元或底線。 不過請注意，以底線開頭的名稱不符合規範[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準。  
  
 下列建議適用於命名。  
  
-   中開始以大寫字母，名稱中的每個個別單字`FindLastRecord`和`RedrawMyForm`。  
  
-   開始函式和方法的名稱，與動詞命令，如同`InitNameArray`或`CloseDialog`。  
  
-   開始類別、 結構、 模組和屬性名稱和名詞，如同`EmployeeName`或`CarAccessory`。  
  
-   開始使用的前置詞的介面名稱"I"，後面接著名詞或名詞片語，例如`IComponent`，或描述之介面的行為，例如形容詞`IPersistable`。 不要使用底線，並且盡量節制，使用縮寫，因為縮寫可能會造成混淆。  
  
-   開始事件處理常式名稱和描述類型的事件，後面接著一個名詞 」`EventHandler`"後置詞，如下所示"`MouseEventHandler`」。  
  
-   在 [名稱]，事件引數類別，包括 「`EventArgs`"後置詞。  
  
-   如果事件的概念 「 之前 」 或 「 之後 」，請使用後置詞中式或過去式，如 「`ControlAdd`「 或 」`ControlAdded`"。  
  
-   使用長或太常使用的詞彙，將名稱長度合理的縮寫，例如"HTML"，而不是 「 超文字標記語言 」。 一般情況下，大於 32 個字元的變數名稱很難讀取設為較低的解析度的監視器上。 此外，請確定您是在整個應用程式一致。 在專案中 「 HTML 」 與 「 超文字標記語言 」 之間隨機切換可能會導致混淆。  
  
-   請避免使用內部範圍中與外部範圍中的名稱相同的名稱。 如果存取錯誤的變數時，可能會造成錯誤。 如果變數與相同名稱的關鍵字之間發生衝突，您必須識別前加上適當的型別程式庫的關鍵字。 例如，如果您有一個名為變數`Date`，您可以使用內建函式`Date`只是藉由呼叫的函式<xref:System.DateTime.Date%2A?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱
- [程式碼中以關鍵字做為項目名稱](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)
