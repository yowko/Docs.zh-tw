---
title: "&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;. Re-implementation of &lt;type&gt; assumed | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42015"
  - "bc42015"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42015"
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;. Re-implementation of &lt;type&gt; assumed
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

衍生類別中的屬性、程序或事件會使用 `Implements` 子句，指定已在基底類別中實作的介面成員。  
  
 衍生類別可以重新實作基底類別所實作的介面成員。  這與覆寫基底類別實作有所不同。  如需詳細資訊，請參閱 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**：BC42015  
  
### 若要更正這個錯誤  
  
-   如果您打算重新實作介面成員，則不需要採取任何動作。  除非您使用 `MyBase` 關鍵字存取基底類別實作，否則衍生類別中的程式碼會存取重新實作的成員。  
  
-   如果您不想重新實作介面成員，請移除屬性、程序或事件宣告中的 `Implements` 子句。  
  
## 請參閱  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)