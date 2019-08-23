---
title: Visual Basic 中的條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 1bee64568ff92468e29226a395f7e5335387e256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945577"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic 中的條件式編譯
在*條件式編譯*中, 程式中的特定程式碼區塊會選擇性地進行編譯, 而有些則會被忽略。  
  
 例如, 您可能會想要撰寫可比較不同方法與相同程式設計工作之速度的偵錯工具, 或者您可能想要將多個語言的應用程式當地語系化。 條件式編譯語句是設計用來在編譯時期執行, 而不是在執行時間執行。  
  
 您可以使用指示詞來表示要有`#If...Then...#Else`條件地編譯的程式碼區塊。 例如, 若要從相同的原始程式碼建立相同應用程式的法文和德文版, 您可以使用預先定義的常數`#If...Then` `FrenchVersion`和`GermanVersion`, 在語句中內嵌平臺特定的程式碼區段。 下列範例示範如何:  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 如果您在編譯時期將`FrenchVersion`條件式編譯常數的值設為`True` , 則會編譯法文版本的條件式程式碼。 如果您將`GermanVersion`常數的值設為`True`, 則編譯器會使用德文版。 如果兩者都未設定`True`為, 則最後一個`Else`區塊中的程式碼會執行。  
  
> [!NOTE]
> 如果程式碼不是最新分支的一部分, 則在編輯程式碼和使用條件式編譯指示詞時, 自動完成將無法運作。  
  
## <a name="declaring-conditional-compilation-constants"></a>宣告條件式編譯常數  
 您可以透過下列三種方式之一來設定條件式編譯常數:  
  
- 在 [**專案設計**工具] 中  
  
- 使用命令列編譯器時, 在命令列中  
  
- 在您的程式碼中  
  
 條件式編譯常數具有特殊範圍, 而且無法從標準程式碼存取。 條件式編譯常數的範圍取決於其設定方式。 下表列出使用上述三種方式宣告的常數範圍。  
  
|如何設定常數|常數的範圍|  
|---|---|  
|**專案設計工具**|專案中所有檔案的公用|  
|命令列|所有傳遞至命令列編譯器的檔案都是公用的|  
|`#Const`程式碼中的語句|私用到其宣告所在的檔案|  
  
|在專案設計工具中設定常數|  
|---|  
|-在建立可執行檔之前, 請遵循[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)中提供的步驟, 在 [**專案設計**工具] 中設定常數。|  
  
|若要在命令列設定常數|  
|---|  
|-使用 **/d**參數輸入條件式編譯常數, 如下列範例所示:<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     **/D**參數和第一個常數之間不需要有空格。 如需詳細資訊, 請參閱[/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)。<br />     命令列宣告會覆寫在 [**專案設計**工具] 中輸入的宣告, 但不會將它們清除。 在 [**專案設計**工具] 中設定的引數會在後續的編譯中繼續生效。<br />     在程式碼本身撰寫常數時, 並沒有任何嚴格的位置規則, 因為其範圍是宣告它們的整個模組。|  
  
|若要在程式碼中設定常數|  
|---|  
|-將常數放在使用它們之模組的宣告區塊中。 這有助於讓您的程式碼井然有序且更容易閱讀。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|---|---|  
|[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|提供讓您的程式碼易於閱讀和維護的建議。|  
  
## <a name="reference"></a>參考資料  
 [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
