---
title: "Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40033"
  - "vbc40033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40033"
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

當介面本身標記為 `<CLSCompliant(False)>` 或未標記時，此介面中的屬性 \(Property\)、程序或事件便會標記為 `<CLSCompliant(True)>`。  
  
 若為符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準的介面，則所有成員都必須符合 CLS 標準。  
  
 當您將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，可以將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。  這個參數沒有預設值，所以您必須提供預設值。  
  
 如果沒有將 <xref:System.CLSCompliantAttribute> 套用至項目，會被認為是不相容。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC40033  
  
### 若要更正這個錯誤  
  
-   如果您需要符合 CLS 標準並能控制介面原始程式碼，若所有成員都符合 CLS 標準，則會將介面標記為 `<CLSCompliant(True)>`。  
  
-   如果您需要符合 CLS 標準但不能控制介面原始程式碼，或者如果它沒有符合的資格，則請在其他介面中定義此成員。  
  
-   如果您需要此成員留在目前的介面中，請從它的定義中移除 <xref:System.CLSCompliantAttribute>，或將它標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)