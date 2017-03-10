---
title: "&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc40035"
  - "bc40035"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40035"
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當程序或屬性覆寫另一個程序或屬性時，程序或屬性標示為 `<CLSCompliant(True)>`，而參數清單之間的唯一差異只在於不規則陣列 \(Jagged Array\) 的巢狀層次或陣列的陣序。  
  
 在下列宣告中，第二個和第三個宣告會產生這個錯誤。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 第二個宣告將原始的一維參數 `arrayParam` 變更為多個陣列的陣列。  第三個宣告則將 `arrayParam` 變更為二維陣列 \(陣序為 2\)。  當 Visual Basic 允許多載之間的不同處只限這些變更的其中一個時，這樣的多載不符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準。  
  
 當您將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，可以將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。  這個參數沒有預設值，所以您必須提供預設值。  
  
 如果沒有將 <xref:System.CLSCompliantAttribute> 套用至項目，會被認為是不相容。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC40035  
  
### 若要更正這個錯誤  
  
-   如果需要符合 CLS 標準，請定義您的多載，讓它們彼此在更多方面不同，而不只限於本說明頁面所舉出的變更。  
  
-   如果您需要多載的差異只限於本說明頁面上所舉出的項目，請從定義移除 <xref:System.CLSCompliantAttribute>，或將它們標示為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)