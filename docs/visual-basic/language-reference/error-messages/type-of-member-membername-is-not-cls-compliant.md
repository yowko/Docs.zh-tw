---
title: "Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40025"
  - "vbc40025"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40025"
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

為此成員指定的資料型別，不屬於 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 的一部分。  這不是元件內的錯誤，因為 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 和 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 都支援這個資料型別。  不過，以嚴格符合 CLS 標準的程式碼撰寫的其他元件，可能無法支援此資料型別。  這類元件可能無法與您的元件順利互動。  
  
 下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別並非 CLS 相容：  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**︰BC40025  
  
### 若要更正這個錯誤  
  
-   如果您的元件只會與其他 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 元件互動，或是完全不與任何其他元件互動，則不需做任何變更。  
  
-   如果您要與不是專為 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 撰寫的元件互動，或許可以透過反映 \(Reflection\) 或從說明文件判斷該元件是否支援此資料型別。  如果會支援，則不需做任何變更。  
  
-   如果您要與不支援這個資料型別的元件互動，則必須以最接近之符合 CLS 標準的型別取代它。  例如，如果數值範圍不需要超過 2,147,483,647，您可以使用 `Integer` 來取代 `UInteger`。  如果真的需要擴充的範圍，可以使用 `Long` 來取代 `UInteger`。  
  
-   如果要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 不同。  例如，`uint` 在其他環境中，通常是 16 位元。  如果您要將 16 位元引數傳遞到這類元件，則需在 Managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中將它宣告為 `UShort`，而不是 `UInteger`。  
  
## 請參閱  
 [反映](../Topic/Reflection%20in%20the%20.NET%20Framework.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)