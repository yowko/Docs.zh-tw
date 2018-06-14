---
title: Visual Basic 中的條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 496df36242c6b43e7e3ec94ce675d11177e8b466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653013"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic 中的條件式編譯
在*條件式編譯*，而忽略其他的特定程式中的程式碼區塊會選擇性地編譯。  
  
 例如，您可能想要撰寫偵錯陳述式比較不同的方法相同的程式設計工作，或您的速度可能會想要當地語系化為多種語言的應用程式。 條件式編譯陳述式被設計為在編譯時期，不在執行階段期間執行。  
  
 代表使用有條件地編譯的程式碼區塊`#If...Then...#Else`指示詞。 例如，若要建立法文及德文語言相同的應用程式，從相同的版本的原始程式碼，內嵌平台專屬的程式碼區段中`#If...Then`陳述式中使用預先定義的常數`FrenchVersion`和`GermanVersion`。 下列範例會示範如何：  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 如果您設定的值`FrenchVersion`條件式編譯常數`True`法文版的條件式程式碼會在編譯時期，編譯。 如果您設定的值`GermanVersion`常數`True`，編譯器會使用德文版。 如果皆未設定`True`，過去的程式碼`Else`封鎖執行。  
  
> [!NOTE]
>  Not 函式時編輯程式碼，並使用條件式編譯指示詞，如果程式碼不是最新分支的一部分，將會自動完成。  
  
## <a name="declaring-conditional-compilation-constants"></a>宣告條件式編譯常數  
 您可以使用三種方式之一來設定條件式編譯常數：  
  
-   在**專案設計工具**  
  
-   在命令列時使用命令列編譯器  
  
-   在您的程式碼  
  
 條件式編譯常數有特殊的範圍，且無法從標準的程式碼存取。 條件式編譯常數的範圍會相依於它的設定方式。 下表列出常數宣告使用上述的三種方式的每個的範圍。  
  
|如何設定常數|常數的範圍|  
|---|---|  
|**專案設計工具**|在專案中的所有檔案公開|  
|命令列|所有檔案公開傳遞至命令列編譯器|  
|`#Const` 在程式碼中的陳述式|私用宣告它的檔案|  
  
|若要設定專案設計工具中的常數|  
|---|  
|-建立之前可執行檔，在中設定常數**專案設計工具**遵循中提供的步驟[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)。|  
  
|若要在命令列設定常數|  
|---|  
|-使用 **/d**切換到輸入條件式編譯常數，如下列範例所示：<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     不不需要之間任何空間 **/d**交換器與第一個常數。 如需詳細資訊，請參閱[/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)。<br />     命令列宣告覆寫中輸入宣告**專案設計工具**，但不是會清除它們。 設定的引數**專案設計工具**對後續編譯仍然有效。<br />     常數寫入時在程式碼本身，沒有嚴格規則對於它們的位置，因為其範圍是整個模組宣告它們。|  
  
|若要在程式碼中設定常數|  
|---|  
|-將宣告區塊中使用的模組中的常數。 這可協助組織更容易閱讀，保持您程式碼。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|---|---|  
|[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|提供讓您輕鬆地閱讀和維護的程式碼的建議。|  
  
## <a name="reference"></a>參考資料  
 [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
