---
title: 印刷樣式與程式碼慣例
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 4906c5ebadb7ce77f2d0e53b2fc5dbab69c5b41f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352706"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>印刷樣式與程式碼慣例 (Visual Basic)

Visual Basic 檔會使用下列印刷樣式和程式碼慣例。  
  
## <a name="typographic-conventions"></a>印刷樣式慣例  
  
|範例|描述|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|特定語言的關鍵字和執行時間成員都有初始大寫字母，而且會格式化，如下列範例所示。|  
|**SmallProject**、 **ButtonCollection**|您所指示類型的單字和片語會格式化，如下列範例所示。|  
|[Module 陳述式](../../visual-basic/language-reference/statements/module-statement.md)|如本範例所示，您可以按一下以移至另一個說明頁的連結。|  
|*object*、 *variableName*、`argumentList`|如本範例所示，您所提供之資訊的預留位置會格式化。|  
|[Shadows]，[ *expressionList* ]|在語法中，選擇性專案會以方括弧括住。|  
|{`Public` &#124; `Friend` &#124; `Private`}|在語法中，當您必須在兩個或多個專案之間進行選擇時，專案會以大括弧括住，並以分隔號分隔。<br /><br /> 您必須只選取一個專案。|  
|[`Protected` &#124; `Friend`]|在語法中，當您可以選擇兩個或多個專案時，這些專案會以方括弧括住，並以分隔號分隔。<br /><br /> 您可以選取專案的任何組合，或沒有專案。|  
|[{`ByVal` &#124; `ByRef`}]|在語法中，如果您可以選取一個以上的專案，但也可以完全省略專案，則專案會以括弧括住，並以分隔號分隔。|  
|*成員名稱*1、*成員名稱*2、*成員*名稱3|相同預留位置的多個實例會以注標區分，如範例中所示。|  
|*成員名稱*<br /><br /> ...<br /><br /> *memberNameN*|在語法中，省略號（...）是用來表示緊接在省略號前面的類型專案數不定。<br /><br /> 在程式碼中，省略號表示為了清楚起見而省略的程式碼。|  
|ESC 鍵，輸入|鍵盤上的索引鍵名稱和按鍵順序會以全部大寫字母顯示。|  
|ALT+F1|當索引鍵名稱之間出現加號（+）時，您必須按住某個按鍵，同時按另一個鍵。 例如，ALT + F1 表示在按下 F1 鍵時按住 ALT 鍵。|  
  
## <a name="code-conventions"></a>程式碼慣例  
  
|範例|描述|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|程式碼範例會以固定音調的字型顯示，格式如下列範例所示。|  
|先前的語句會將 `sampleString` 的值設定為 "Hello，world！"|解說文字中的程式碼專案會以固定音調的字型顯示，如下列範例所示。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|程式碼批註是以單引號（'）或 REM 關鍵字引進。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|在行尾加上底線（_）的空格表示語句會繼續在下面這一行。|  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 語言參考](../../visual-basic/language-reference/index.md)
- [關鍵字](../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 執行階段程式庫成員](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic 命名慣例](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [操作說明：在程式碼內中斷和合併陳述式](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [程式碼中的註解](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
