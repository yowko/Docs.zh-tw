---
title: 名稱 <membername> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 43fff3f12295f3837148b0a349887e8405126819
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160232"
---
# <a name="bc40031-name-membername-is-not-cls-compliant"></a>BC40031：名稱 \<membername> 不符合 CLS 規範

元件會標示為， `<CLSCompliant(True)>` 但會使用開頭為底線 () 的名稱來公開成員 `_` 。

 程式設計專案可以包含一或多個底線，但為了符合 Language-Independent 的 [語言獨立性和](../../../standard/language-independence-and-language-independent-components.md) (cls) 的元件，它不能以底線開頭。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。

 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。

 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC40031

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您有原始程式碼的控制權，請變更成員名稱，使它不是以底線開頭。

- 如果您要求成員名稱保持不變，請 <xref:System.CLSCompliantAttribute> 從其定義中移除，或將它標示為 `<CLSCompliant(False)>` 。 您仍然可以將元件標示為 `<CLSCompliant(True)>` 。

## <a name="see-also"></a>另請參閱

- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic 命名慣例](../../programming-guide/program-structure/naming-conventions.md)
