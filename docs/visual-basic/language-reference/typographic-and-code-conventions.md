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
ms.openlocfilehash: 3255dff8268cd5500a1244716f37bf30f5b43cfb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828624"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>印刷樣式與程式碼慣例 (Visual Basic)
Visual Basic 文件會使用下列的印刷樣式和程式碼慣例。  
  
## <a name="typographic-conventions"></a>印刷樣式慣例  
  
|範例|描述|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|特定語言關鍵字和執行階段成員具有第一個字母大寫，並在此範例中所示的格式。|  
|**SmallProject**， **ButtonCollection**|在此範例中所示，會格式化單字和片語系統指示您輸入。|  
|[Module 陳述式](../../visual-basic/language-reference/statements/module-statement.md)|在此範例中所示，您可以按一下以移至另一個 [說明] 頁面的連結會格式化。|  
|*object*, *variableName*, `argumentList`|在此範例中所示，會格式化預留位置，如您所提供的資訊。|  
|[陰影]、 [ *expressionList* ]|在語法中，選擇性的項目會括在方括號。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|在語法中，當您必須選擇兩個或多個項目，項目會大括號括住，並以分隔號分隔。<br /><br /> 您必須選取其中一個，而且是唯一一個項目。|  
|[ `Protected` &#124; `Friend` ]|在語法中，當您有兩個或多個項目之間所選取的選項的項目會以方括弧括住，和以分隔號分隔。<br /><br /> 您可以選取任何項目組合的或沒有任何項目。|  
|[{ `ByVal` &#124; `ByRef` }]|在語法中，您可以選取一個以上的項目，但您也可以完全省略項目時項目是以方括弧括住以大括號括住並以分隔號分隔。|  
|*memberName*1， *memberName*2 *memberName*3|多個執行個體的相同預留位置的差別在於註標，如範例所示。|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|在語法中，省略符號 （...） 用來指示不定數目的省略符號前面的立即種類的項目。<br /><br /> 在程式碼中省略符號表示為求清楚起見省略的程式碼。|  
|ESC 鍵，輸入|索引鍵名稱和鍵盤上的索引鍵序列會出現以全部大寫的字母。|  
|ALT+F1|當索引鍵名稱之間，會出現加號 （+） 時，您必須按住一個按鍵同時按下其他。 比方說，ALT + F1 表示按住 ALT 鍵，同時按下 F1 鍵。|  
  
## <a name="code-conventions"></a>程式碼慣例  
  
|範例|描述|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|程式碼範例會出現在固定字幅的字型，而且在此範例中所示的格式。|  
|前一個陳述式設定的值`sampleString`以"Hello，world ！"|在此範例中所示，說明文字中的程式碼項目會出現在固定字幅的字型。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|單引號 （'） 或 REM 關鍵字所導入程式碼註解。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|空格，後面接著底線 (_) 行結尾指出陳述式會繼續到下一行。|  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 語言參考](../../visual-basic/language-reference/index.md)
- [關鍵字](../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 執行階段程式庫成員](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic 命名慣例](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [如何：在程式碼內中斷和合併陳述式](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [程式碼中的註解](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
