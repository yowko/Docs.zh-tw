---
title: "選擇性的值為選擇性參數的型別&lt;parametername&gt;不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
dev_langs:
- VB
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 3dbcab01022d1604e79c6bfc3e04a14ef60bc219
ms.lasthandoff: 03/13/2017

---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>選擇性的值為選擇性參數的型別&lt;parametername&gt;不符合 CLS 標準
程序已標記為 `<CLSCompliant(True)>`，但所宣告的 [Optional](../../../visual-basic/language-reference/modifiers/optional.md) 參數卻具有不符合標準之型別的預設值。  
  
 程序必須只使用符合 CLS 標準的型別，才能夠符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3) (CLS) 標準。 這適用於參數型別、傳回型別及其所有區域變數的型別。 它也適用於選擇性參數的預設值。  
  
 下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 資料類型不符合 CLS 標準：  
  
-   [SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 當您將套用<xref:System.CLSCompliantAttribute>屬性程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute> 這個參數沒有預設值，您必須提供值。  
  
 如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：**BC40042  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   選擇性的參數都必須有此特定型別的預設值，如果移除<xref:System.CLSCompliantAttribute>.</xref:System.CLSCompliantAttribute> 程序不符合 CLS 規範。  
  
-   如果程序必須符合 CLS 標準，請將這個預設值的型別變更為最符合 CLS 標準的型別。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
-   如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中的資料寬度不同。 例如，`int` 在其他環境中通常是 16 位元。 如果您所接收的是來自這類元件的 16 位元整數，請在您的 Managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式碼中將它宣告為 `Short` 而不是 `Integer`。  
  
## <a name="see-also"></a>另請參閱  
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
