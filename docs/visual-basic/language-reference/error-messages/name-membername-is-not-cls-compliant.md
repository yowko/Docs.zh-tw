---
title: "Name &lt;membername&gt; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40031"
  - "vbc40031"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40031"
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Name &lt;membername&gt; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

組件 \(Assembly\) 會標記為 `<CLSCompliant(True)>`，但會公開 \(Expose\) 其名稱是以底線 \(`_`\) 開頭的成員。  
  
 程式設計的項目可以包含一個以上的底線，但若要符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準，則不能以底線開頭。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 當您將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，可以將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。  這個參數沒有預設值，所以您必須提供預設值。  
  
 如果沒有將 <xref:System.CLSCompliantAttribute> 套用至項目，會被認為是不相容。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID︰**BC40031  
  
### 若要更正這個錯誤  
  
-   如果您具有原始程式碼的控制權，請將成員名稱變更為不是以底線開頭。  
  
-   如果需要成員名稱保持不變，請從它的定義中移除 <xref:System.CLSCompliantAttribute>，或將它標記為 `<CLSCompliant(False)>`。  您仍然可以將組件標記為 `<CLSCompliant(True)>`。  
  
## 請參閱  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)