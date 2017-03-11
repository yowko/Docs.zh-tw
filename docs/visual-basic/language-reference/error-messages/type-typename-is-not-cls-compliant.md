---
title: "Type &lt;typename&gt; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40041"
  - "vbc40041"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40041"
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Type &lt;typename&gt; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

以不符合 CLS 標準的資料型別，宣告變數、屬性 \(Property\) 或函式傳回。  
  
 應用程式必須只使用符合 CLS 標準的型別，才能符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準。  
  
 下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別並非 CLS 相容：  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **錯誤 ID︰**BC40041  
  
### 若要更正這個錯誤  
  
-   如果應用程式需要符合 CLS 標準，請將這個項目的資料型別變更為最符合 CLS 標準的型別。  例如，如果數值範圍不需要超過 2,147,483,647，您可以使用 `Integer` 來取代 `UInteger`。  如果真的需要擴充的範圍，可以使用 `Long` 來取代 `UInteger`。  
  
-   如果您的應用程式不需要符合 CLS 標準，則不需要變更任何項目。  不過，您應該留意不相容的問題。  
  
## 請參閱  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)