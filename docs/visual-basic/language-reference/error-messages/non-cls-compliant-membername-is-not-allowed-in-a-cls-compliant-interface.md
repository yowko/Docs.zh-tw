---
title: 非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: ee533df5e06352034b24651b9173a88d090da0a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許
屬性、 程序或在介面中的事件標記為`<CLSCompliant(True)>`當介面本身標示為`<CLSCompliant(False)>`或未標記。  
  
 若要符合介面[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準，其所有成員都必須相容。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40033  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您需要 cls 符合性，而且能夠控制介面原始程式碼，標記為介面`<CLSCompliant(True)>`如果其所有成員都均相容。  
  
-   如果您需要 cls 符合性，而且不需要控制介面的原始碼，或是它不符合標準，定義這個成員在不同的介面。  
  
-   如果您想要將這個成員保留其目前的介面中，移除<xref:System.CLSCompliantAttribute>從其定義或將其標記為`<CLSCompliant(False)>`。  
  
## <a name="see-also"></a>另請參閱  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
