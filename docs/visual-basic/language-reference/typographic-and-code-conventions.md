---
title: 印刷樣式與程式碼慣例 (Visual Basic)
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
ms.openlocfilehash: eb7a33ef21bf6beda730dffa8eb7ff9cabe599fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604493"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>印刷樣式與程式碼慣例 (Visual Basic)
Visual Basic 文件使用下列印刷樣式與程式碼慣例。  
  
## <a name="typographic-conventions"></a>印刷樣式慣例  
  
|範例|描述|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|語言特有的關鍵字和執行階段成員具有第一個字母大寫，而且會格式化為此範例所示。|  
|**SmallProject**， **ButtonCollection**|單字和片語指示您輸入的格式，如同此範例所示。|  
|[Module 陳述式](../../visual-basic/language-reference/statements/module-statement.md)|您可以按一下以移至另一個說明頁面的連結會格式化為此範例所示。|  
|*物件*， *variableName*， `argumentList`|您提供的資訊的預留位置的格式，如同此範例所示。|  
|[陰影]、 [ *expressionList* ]|在語法中，選用項目會放在括號。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|在語法中，當您必須做出選擇兩個或多個項目之間的項目會括在大括弧和以分隔號分隔。<br /><br /> 您必須選取其中一個，而且只有一個，項目。|  
|[ `Protected` &#124; `Friend` ]|在語法中，當您有兩個或多個項目之間選擇時的項目會以方括弧括住，和以分隔號分隔。<br /><br /> 您可以選取任何項目組合的或任何項目。|  
|[{ `ByVal` &#124; `ByRef` }]|在語法中，您可以選取一個以上的項目，但您也可以完整地忽略這些項目時項目會以方括弧括住以大括號括住並以分隔號分隔。|  
|*memberName*1， *memberName*2， *memberName*3|此範例中所示註標，來區分相同預留位置的多個執行個體。|  
|*1>*<br /><br /> ...<br /><br /> *memberNameN*|在語法中，省略符號 （...） 用來指示了不定數量的項目之前的種類。<br /><br /> 在程式碼中省略符號表示省略為避免混淆的程式碼。|  
|ESC 鍵，請輸入|索引鍵的名稱和鍵盤上的索引鍵序列顯示全部大寫的字母。|  
|ALT + F1|當索引鍵名稱之間，會顯示加號 （+） 時，必須在時按下其他按住一個索引鍵。 例如，ALT + F1 表示按住 ALT 鍵，同時按下 F1 鍵。|  
  
## <a name="code-conventions"></a>程式碼慣例  
  
|範例|描述|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|程式碼範例會出現在固定字幅的字型，而且會格式化為此範例所示。|  
|前一個陳述式設定的值`sampleString`以"Hello，world ！"|說明文字中的程式碼項目出現固定字幅的字型，此範例所示。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|程式碼註解會以單引號 （'） 或 REM 關鍵字引入。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|空格，後面接著底線 (_) 行結尾指出陳述式會繼續到下一行。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 語言參考](../../visual-basic/language-reference/index.md)  
 [關鍵字](../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic 執行階段程式庫成員](../../visual-basic/language-reference/runtime-library-members.md)  
 [Visual Basic 命名慣例](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [操作說明：在程式碼內中斷和合併陳述式](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [程式碼中的註解](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
