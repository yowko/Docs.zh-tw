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
ms.openlocfilehash: b25d246bd31147b7a9ba2c72214926fdb5ca8895
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072141"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic 命名慣例

當您在 Visual Basic 應用程式中為元素命名時，該名稱的第一個字元必須是字母字元或底線。 不過請注意，以底線開頭的名稱，不符合 [語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (cls) 。  
  
 下列建議適用于命名。  
  
- 使用大寫字母在名稱中開始每個個別單字，如同 `FindLastRecord` 和 `RedrawMyForm` 。  
  
- 使用動詞來開始函式和方法名稱，如 `InitNameArray` 或 `CloseDialog` 。  
  
- 以名詞開頭的類別、結構、模組和屬性名稱，如 `EmployeeName` 或 `CarAccessory` 。  
  
- 以前置詞 "I" 開頭的介面名稱開頭，後面接著名詞或名詞片語，例如 `IComponent` ，或使用描述介面行為的形容詞（例如） `IPersistable` 。 請勿使用底線，並謹慎使用縮寫，因為縮寫可能會造成混淆。  
  
- 以名詞開頭的事件處理常式名稱，後面接著 " `EventHandler` " 尾碼（如同 " `MouseEventHandler` "）。  
  
- 在事件引數類別的名稱中，包含 " `EventArgs` " 尾碼。  
  
- 如果事件有 "before" 或 "after" 的概念，請在現有或過去的時態中使用後置詞，如 " `ControlAdd` " 或 " `ControlAdded` "。  
  
- 若為長或經常使用的字詞，請使用縮寫讓名稱長度保持合理，例如「HTML」，而不是「超文字標記語言 (HTML) 」。 一般情況下，大於32個字元的變數名稱，在設定為低解析度的監視器上很難讀取。 此外，請確定您的縮寫在整個應用程式中都是一致的。 在「HTML」和「超文字標記語言 (HTML) 」之間隨機切換專案可能會造成混淆。  
  
- 避免在內部範圍中使用與外部範圍中的名稱相同的名稱。 如果存取錯誤的變數，就會產生錯誤。 如果變數與相同名稱的關鍵字之間發生衝突，您必須在其前面加上適當的類型程式庫來識別關鍵字。 例如，如果您有一個名為的變數 `Date` ，您只能藉由呼叫來使用內部 `Date` 函數 <xref:System.DateTime.Date%2A?displayProperty=nameWithType> 。  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的項目名稱關鍵字](keywords-as-element-names-in-code.md)
- [Me、My、MyBase 及 MyClass](me-my-mybase-and-myclass.md)
- [Declared Element Names](../language-features/declared-elements/declared-element-names.md)
- [程式結構和程式碼慣例](program-structure-and-code-conventions.md)
- [Visual Basic 語言參考](../../language-reference/index.md)
