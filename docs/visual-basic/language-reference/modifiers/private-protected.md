---
title: 私用受保護的 (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a>私用受保護的 (Visual Basic)

`Private Protected`關鍵字的組合都是成員的存取修飾詞。 A`Private Protected`成員是可存取它的包含類別中的所有成員，以及衍生自包含類別，但前提是其包含的組件中找到。 

您可以指定`Private Protected`只成員上的類別; 無法套用`Private Protected`結構的成員因為結構無法被繼承。

`Private Protected`存取修飾詞支援的 Visual Basic 15.5 和更新版本。 若要使用它，您可以將下列項目加入 Visual Basic 專案 (*.vbproj) 檔。 只要 Visual Basic 15.5 或更新版本安裝在您的系統上，它可讓您充分利用所有最新版本的 Visual Basic 編譯器所支援的語言功能：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> 在 Visual Studio 中，選取 F1 說明上`private protected`提供任何說明[私人](private.md)或[保護](protected.md)。 IDE 會挑選單一語彙基元，在資料指標，而不是複合字。

## <a name="rules"></a>規則

- **宣告內容。** 您可以使用`Private Protected`只能在類別層級。 這表示宣告內容`Protected`項目必須是類別，且不能原始程式檔、 命名空間、 介面、 模組、 結構或程序。

## <a name="behavior"></a>行為

- **存取層級。** 類別中的所有程式碼可以存取其項目。 任何衍生自基底類別，而且會包含在相同的組件的類別中的程式碼可以存取所有`Private Protected`基底類別的項目。 不過，在任何類別，衍生自基底類別，而且會包含在不同的組件中的程式碼無法存取基底類別`Private Protected`項目。

- **存取修飾詞。** 指定存取層級的關鍵字稱為*存取修飾詞*。 如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。
  
 `Private Protected` 修飾詞可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)的巢狀類別  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)委派的巢狀類別中  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)eumeration 巢狀類別中 
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)介面的巢狀類別中 
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [結構陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)結構的巢狀類別中 
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Protected 的 Friend](./protected-friend.md)   
[在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
