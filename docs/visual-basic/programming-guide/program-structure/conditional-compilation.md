---
title: Visual Basic 中的條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 828edf2e5491394f5ac802b5c9babfb3df359e59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758453"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic 中的條件式編譯
在 *條件式編譯*，而忽略其他特定的程式中的程式碼區塊會選擇性地編譯。  
  
 例如，您可能想要撰寫偵錯陳述式，比較不同的方法相同的程式設計工作，或您的速度可能會想要將應用程式在多國語言的當地語系化。 條件式編譯陳述式被設計為在編譯期間，不是在執行階段執行。  
  
 表示有條件地編譯的程式碼區塊`#If...Then...#Else`指示詞。 比方說，若要建立法文及德文語言版本相同的應用程式，從相同來源的程式碼，您將內嵌平台特定程式碼區段中的`#If...Then`陳述式使用預先定義的常數`FrenchVersion`和`GermanVersion`。 下列範例示範如何：  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 如果您設定的值`FrenchVersion`條件式編譯常數，以`True`在編譯時期，法文版的條件式程式碼會編譯。 如果您設定的值`GermanVersion`常數`True`，編譯器會使用德文版。 如果沒有設定任何`True`，在過去的程式碼`Else`封鎖執行。  
  
> [!NOTE]
>  Not 函式時編輯程式碼，並使用條件式編譯指示詞，如果程式碼不是最新分支的一部分，將會自動完成。  
  
## <a name="declaring-conditional-compilation-constants"></a>宣告條件式編譯常數  
 您可以使用三種方式之一來設定條件式編譯常數：  
  
- 在 **專案設計工具**  
  
- 在命令列使用命令列編譯器時  
  
- 在您的程式碼  
  
 條件式編譯常數有特殊的範圍，並不能從標準的程式碼存取。 條件式編譯常數的範圍是取決於它的設定方式。 下表列出使用每個先前所述的三種方式宣告的常數的範圍。  
  
|如何設定常數|常數的範圍|  
|---|---|  
|**專案設計工具**|公用專案中的所有檔案|  
|命令列|公開的所有檔案傳遞至命令列編譯器|  
|`#Const` 在程式碼中的陳述式|私人雲端擴充到宣告它的檔案|  
  
|若要設定 專案設計工具中的常數|  
|---|  
|之前建立可執行檔，請在中設定常數**專案設計工具**依照所提供的步驟[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)。|  
  
|若要在命令列設定常數|  
|---|  
|-使用 **/d**切換到輸入條件式編譯常數，如下列範例所示：<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     不不需要之間任何空間 **/d**交換器與第一個常數。 如需詳細資訊，請參閱 < [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)。<br />     命令列宣告覆寫輸入中的宣告**專案設計工具**，但不是會將它們清除。 在 設定引數**專案設計工具**對後續編譯仍然有效。<br />     當撰寫程式碼本身中的常數，沒有嚴格的規則，對於其放置的功能，因為它們的範圍是整個模組在宣告。|  
  
|若要設定您的程式碼中的常數|  
|---|  
|-將放在其中使用的模組宣告區塊中的常數。 如此一來，可協助組織更容易閱讀，確保您的程式碼。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|---|---|  
|[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|提供讓您輕鬆地閱讀和維護的程式碼的建議。|  
  
## <a name="reference"></a>參考資料  
 [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
