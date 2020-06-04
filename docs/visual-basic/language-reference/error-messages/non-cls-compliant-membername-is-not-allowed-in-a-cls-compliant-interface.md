---
title: 符合 CLS 標準的介面中不允許有不符合 CLS 標準的 <membername>
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409396"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>符合 CLS 標準的介面中不允許有不符合 CLS 標準的 \<membername>
介面中的屬性、程式或事件會標記為 `<CLSCompliant(True)>` 介面本身標記為 `<CLSCompliant(False)>` 或未標記時。  
  
 若要讓介面符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS），其所有成員都必須符合規範。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC40033  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您需要 CLS 符合性，而且可以控制介面原始程式碼，請將介面標示為 `<CLSCompliant(True)>` 符合其所有成員的規範。  
  
- 如果您需要 CLS 合規性，而且無法控制介面原始程式碼，或如果不符合規範，請在不同的介面中定義這個成員。  
  
- 如果您要求這個成員保留在其目前的介面中，請 <xref:System.CLSCompliantAttribute> 從其定義中移除，或將其標記為 `<CLSCompliant(False)>` 。  
  
## <a name="see-also"></a>另請參閱

- [Interface 陳述式](../statements/interface-statement.md)
