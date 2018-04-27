---
title: 參數的型別&#39; &lt;parametername&gt; &#39;不符合 CLS 標準
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d34de9e5914b02a0e878b87e786b81a5940a6d85
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>參數的型別&#39; &lt;parametername&gt; &#39;不符合 CLS 標準
程序標示為`<CLSCompliant(True)>`但會宣告參數的型別標示為`<CLSCompliant(False)>`、 未標示，或因為它是不相容的類型而不符資格。  
  
 程序必須只使用符合 CLS 規範的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。 這適用於參數型別、傳回型別及其所有區域變數的型別。  
  
 下列 Visual Basic 資料類型不符合 CLS 標準：  
  
-   [SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40028  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果程序必須接受這個特定類型的參數，移除<xref:System.CLSCompliantAttribute>。 程序不符合 CLS 規範。  
  
-   如果該程序必須符合 CLS 標準，將此參數的型別變更為最接近的符合 CLS 標準類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
-   如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中的資料寬度不同。 例如，`int` 在其他環境中通常是 16 位元。 如果您接受這類元件從 16 位元整數，將它宣告為`Short`而不是`Integer`受管理的 Visual Basic 程式碼。