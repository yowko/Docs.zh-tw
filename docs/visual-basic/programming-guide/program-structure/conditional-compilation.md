---
title: "Conditional Compilation in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional compilation, about conditional compilation"
  - "compilation, conditional"
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conditional Compilation in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在「*條件式編譯*」\(Conditional Compilation\) 中，會選擇性地編譯程式中的特定程式碼區塊，而忽略其他的程式碼區塊。  
  
 例如，您可能想要撰寫以不同方法執行相同程式工作間速度比較的偵錯陳述式，或想將應用程式當地語系化成不同的語言。  條件式編譯陳述式 \(Statement\) 是設計於編譯時間執行，而不是在執行階段執行。  
  
 您可以用 `#If...Then...#Else` 指示詞來表示要有條件地編譯的程式碼區塊。  例如，若要從相同的原始程式碼建立同一個應用程式的法文和德文版本，您可以使用預先定義的常數 `FrenchVersion` 和 `GermanVersion`，在 `#If...Then` 陳述式 \(Statement\) 中嵌入特定平台的程式碼區段。  如下列範例所示：  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 如果您在編譯時期將 `FrenchVersion` 條件式編譯常數的值設定為 `True`，則會編譯法文版的條件式程式碼。  如果將 `GermanVersion` 常數的值設定為 `True`，編譯器就會使用德文版。  如果兩者都未設定為 `True`，則會執行最後一個 `Else` 區塊中的程式碼。  
  
> [!NOTE]
>  如果程式碼不是目前分支的一部分，則在編輯程式碼和使用條件式編譯指示詞時，自動完成不會運作。  
  
## 宣告條件式編譯常數  
 您可以利用下列三種方法的其中一個來設定條件式編譯常數：  
  
-   在 \[**專案設計工具**\] 中  
  
-   在命令列中，當您使用命令列編譯器時  
  
-   在程式碼中  
  
 條件式編譯常數有特殊的範圍，無法自標準碼存取。  條件式編譯常數的範圍取決於它的設定方式。  下表列出以上述三種方式宣告的常數之範圍。  
  
|||  
|-|-|  
|常數設定方式|常數範圍|  
|**專案設計工具**|對專案中所有檔案公開|  
|命令列|對所有傳遞至命令列編譯器的檔案公開|  
|程式碼中的 `#Const` 陳述式|只對它在其中宣告的檔案公開|  
  
||  
|-|  
|若要在專案設計工具中設定常數|  
|-   在建立可執行檔之前，請先依照 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)中所提供的步驟，在 \[**專案設計工具**\] 中設定常數。|  
  
||  
|-|  
|若要在命令列中設定常數|  
|-   使用 **\/d** 切換控制來輸入條件式編譯常數，如下列範例所示：<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     **\/d** 切換控制與第一個常數之間不需要空格。  如需詳細資訊，請參閱 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)。<br />     命令列宣告會覆寫在 \[**專案設計工具**\] 中輸入的宣告，但是不會將它們清除。  在 \[**專案設計工具**\] 中設定的引數，對後續的編譯仍然有效。<br />     將常數寫入程式碼本身時，對它們的位置並沒有嚴格規則 \(Rule\)，因為它們的範圍是它們在其中被宣告的整個模組。|  
  
||  
|-|  
|若要在程式碼中設定常數|  
|-   將常數放在使用它們的模組中之宣告區塊。  這樣可使您的程式碼有組織並容易閱讀。|  
  
## 相關主題  
  
|||  
|-|-|  
|標題|描述|  
|[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|提供讓您的程式碼易於讀取及維護的建議。|  
  
## 參考資料  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)