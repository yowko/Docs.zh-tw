---
title: 命名規範
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
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347314"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic 命名慣例
當您在 Visual Basic 應用程式中為元素命名時，該名稱的第一個字元必須是字母字元或底線。 不過，請注意，以底線開頭的名稱不符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）。  
  
 下列建議適用于命名。  
  
- 以大寫字母開頭，名稱中的每個個別單字，如 `FindLastRecord` 和 `RedrawMyForm`。  
  
- 使用動詞來開始函式和方法名稱，如 `InitNameArray` 或 `CloseDialog`。  
  
- 以名詞開頭的類別、結構、模組和屬性名稱，如 `EmployeeName` 或 `CarAccessory`。  
  
- 以前置詞 "I" 開頭，後面接著名詞或名詞片語（例如 `IComponent`），或使用描述介面行為（例如 `IPersistable`）的形容詞來開始介面名稱。 請勿使用底線，並謹慎使用縮寫，因為縮寫可能會造成混淆。  
  
- 以名詞開頭的事件處理常式名稱，描述後面接著 "`EventHandler`" 後置詞的事件種類，如 "`MouseEventHandler`"。  
  
- 在事件引數類別的名稱中，包含 "`EventArgs`" 尾碼。  
  
- 如果事件具有 "before" 或 "after" 的概念，請使用存在或過去時態的尾碼，如 "`ControlAdd`" 或 "`ControlAdded`"。  
  
- 若為長時間或經常使用的詞彙，請使用縮寫來保留名稱長度合理，例如 "HTML"，而不是 "超文字標記語言 (HTML)"。 一般而言，大於32個字元的變數名稱很容易讀取到設定為低解析度的監視器上。 此外，請確定您的縮寫在整個應用程式中都是一致的。 在「HTML」和「超文字標記語言 (HTML)」之間隨機切換專案可能會造成混淆。  
  
- 避免在內部範圍中使用與外部範圍中的名稱相同的名稱。 如果存取錯誤的變數，可能會產生錯誤。 如果變數與相同名稱的關鍵字之間發生衝突，您必須在其前面加上適當的類型程式庫，以識別關鍵字。 例如，如果您有一個稱為 `Date`的變數，您只能藉由呼叫 <xref:System.DateTime.Date%2A?displayProperty=nameWithType>來使用內建 `Date` 函數。  
  
## <a name="see-also"></a>請參閱

- [程式碼中以關鍵字做為項目名稱](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)
