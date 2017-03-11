---
title: "Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40027"
  - "vbc40027"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40027"
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`Function` 程序已標記為 `<CLSCompliant(True)>`，但傳回的型別因為是不符合標準的型別，而標記為 `<CLSCompliant(False)>`、沒有標記或不符合資格。  
  
 程序必須只使用符合 CLS 標準的型別，才能夠符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準。  這適用於參數型別、傳回型別及其所有區域變數的型別。  
  
 下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別並非 CLS 相容：  
  
-   [SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 當您將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，可以將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。  這個參數沒有預設值，所以您必須提供預設值。  
  
 如果沒有將 <xref:System.CLSCompliantAttribute> 套用至項目，會被認為是不相容。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID︰**BC40027  
  
### 若要更正這個錯誤  
  
-   如果 `Function` 程序必須傳回這個特定型別，請移除 <xref:System.CLSCompliantAttribute>。  程序不可符合 CLS 標準。  
  
-   如果 `Function` 程序必須符合 CLS 標準，則需將傳回型別變更為最接近之符合 CLS 標準的型別。  例如，如果數值範圍不需要超過 2,147,483,647，您可以使用 `Integer` 來取代 `UInteger`。  如果真的需要擴充的範圍，可以使用 `Long` 來取代 `UInteger`。  
  
-   如果要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 不同。  例如，`int` 在其他環境中，通常是 16 位元。  如果您要將 16 位元整數傳回給這類元件，則需在 Managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中將它宣告為 `Short`，而不是 `Integer`。  
  
## 請參閱  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)