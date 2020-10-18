---
title: 符合 CLS 標準的介面中不允許有不符合 CLS 標準的 <membername>
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: aa7944e90857436553435ce783c0820770496a49
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159985"
---
# <a name="bc40033-non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>BC40033： \<membername> 符合 cls 標準的介面中不允許不符合 cls 規範

介面中的屬性、程式或事件會標示為 `<CLSCompliant(True)>` 介面本身標示為或未標記的時機 `<CLSCompliant(False)>` 。

 為了讓介面符合 [語言獨立性，以及](../../../standard/language-independence-and-language-independent-components.md) (CLS) 的 Language-Independent 元件，其所有成員都必須符合規範。

 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。

 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC40033

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您需要 CLS 符合性，而且可以控制介面原始程式碼，請將介面標示為 `<CLSCompliant(True)>` 符合其所有成員的規範。

- 如果您需要 CLS 符合性，而且沒有介面原始程式碼的控制權，或者如果它不符合規範，請在不同的介面內定義這個成員。

- 如果您要求這個成員維持在其目前的介面中，請 <xref:System.CLSCompliantAttribute> 從其定義中移除，或將它標示為 `<CLSCompliant(False)>` 。

## <a name="see-also"></a>另請參閱

- [Interface 陳述式](../statements/interface-statement.md)
