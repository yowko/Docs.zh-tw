---
title: 條件式編譯
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e59296882edc018259816c73b6ae861b3b296783
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098965"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic 中的條件式編譯

在 *條件式編譯*中，程式中的特定程式碼區塊會選擇性地編譯，而其他區塊則會被忽略。  
  
 例如，您可能想要撰寫偵錯工具來比較不同方法與相同程式設計工作的速度，或您可能想要將多個語言的應用程式當地語系化。 條件式編譯語句是設計成在編譯期間執行，而不是在執行時間執行。  
  
 您可以使用指示詞來表示要有條件地編譯的程式碼區塊 `#If...Then...#Else` 。 例如，若要從相同的原始程式碼建立相同應用程式的法文和德文語言版本，您可以 `#If...Then` 使用預先定義的常數和，在語句中內嵌平臺特定的程式碼區段 `FrenchVersion` `GermanVersion` 。 下列範例示範如何：  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 如果您在 `FrenchVersion` 編譯時期將條件式編譯常數的值設定為 `True` ，則會編譯法文版本的條件式程式碼。 如果您將常數的值設定 `GermanVersion` 為 `True` ，則編譯器會使用德文版。 如果兩個都未設定為，則會 `True` 執行最後一個區塊中的程式碼 `Else` 。  
  
> [!NOTE]
> 如果程式碼不是最新分支的一部分，則在編輯程式碼和使用條件式編譯指示詞時，自動完成功能將無法運作。  
  
## <a name="declaring-conditional-compilation-constants"></a>宣告條件式編譯常數  

 您可以透過下列三種方式之一來設定條件式編譯常數：  
  
- 在**專案設計**工具中  
  
- 使用命令列編譯器時的命令列  
  
- 在您的程式碼中  
  
 條件式編譯常數具有特殊範圍，無法從標準程式碼存取。 條件式編譯常數的範圍取決於其設定方式。 下表列出使用上述三種方法宣告的常數範圍。  
  
|常數的設定方式|常數的範圍|  
|---|---|  
|**專案設計工具**|公用至專案中的所有檔案|  
|命令列|公用至傳遞至命令列編譯器的所有檔案|  
|`#Const` 程式碼中的語句|私用至其宣告所在的檔案|  
  
|在專案設計工具中設定常數|  
|---|  
|-在建立可執行檔之前，請遵循[管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)中提供的步驟，在**專案設計**工具中設定常數。|  
  
|若要在命令列設定常數|  
|---|  
|-使用 **-d** 參數來輸入條件式編譯常數，如下列範例所示：<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     **-D**參數和第一個常數之間不需要空格。 如需詳細資訊，請參閱 [-定義 (Visual Basic) ](../../reference/command-line-compiler/define.md)。<br />     命令列宣告會覆寫在 [ **專案設計**工具] 中輸入的宣告，但不會將它們清除。 在 [ **專案設計** 工具] 中設定的引數在後續的編譯中仍有效。<br />     撰寫程式碼本身的常數時，不會有嚴格的規則來放置它們，因為其範圍是宣告它們的整個模組。|  
  
|若要在您的程式碼中設定常數|  
|---|  
|-將常數放在其所使用之模組的宣告區塊中。 這有助於讓您的程式碼井然有序且更容易閱讀。|  
  
## <a name="related-topics"></a>[相關主題]  
  
|Title|描述|  
|---|---|  
|[程式結構和程式碼慣例](program-structure-and-code-conventions.md)|提供讓您的程式碼更容易讀取和維護的建議。|  
  
## <a name="reference"></a>參考  

 [#Const 指示詞](../../language-reference/directives/const-directive.md)  
  
 [#If .。。Then ... #Else 指示詞](../../language-reference/directives/if-then-else-directives.md)  
  
 [-定義 (Visual Basic) ](../../reference/command-line-compiler/define.md)
