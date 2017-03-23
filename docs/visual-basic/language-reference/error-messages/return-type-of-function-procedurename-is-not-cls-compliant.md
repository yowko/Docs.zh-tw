---
title: "函式的傳回型別 &quot;&lt;m e&gt;&quot; 不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
dev_langs:
- VB
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 99a07393d976dc99998b29d2ba2cd7d554ec1bad
ms.lasthandoff: 03/13/2017

---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a>函式的傳回型別 '&lt;m e&gt;' 不符合 CLS 標準
A`Function`程序會標示為`<CLSCompliant(True)>`，但會傳回型別標示為`<CLSCompliant(False)>`、 未標記，或因為它是不相容的類型不符合。  
  
 程序必須只使用符合 CLS 規範的型別，才能夠符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3) (CLS) 標準。 這適用於參數型別、傳回型別及其所有區域變數的型別。  
  
 下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 資料類型不符合 CLS 規範：  
  
-   [SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute> 這個參數沒有預設值，您必須提供值。  
  
 如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40027  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果`Function`程序必須傳回此特定的型別、 移除<xref:System.CLSCompliantAttribute>.</xref:System.CLSCompliantAttribute> 程序不符合 CLS 規範。  
  
-   如果`Function`程序必須是符合 CLS 標準，將傳回的型別變更為最符合 CLS 標準的型別。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
-   如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中的資料寬度不同。 例如，`int` 在其他環境中通常是 16 位元。 如果傳回 16 位元整數的這類元件，將它宣告為`Short`而不是`Integer`中 managed[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
