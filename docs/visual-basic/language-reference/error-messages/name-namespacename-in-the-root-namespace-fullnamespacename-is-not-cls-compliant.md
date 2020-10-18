---
title: 根命名空間 <namespacename> 中的名稱 <fullnamespacename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 48e020cb74641279a4f402e47034514d78dfc4fc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160206"
---
# <a name="bc40039-name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>BC40039： \<namespacename> 根命名空間中的名稱 \<fullnamespacename> 不符合 CLS 規範

元件標示為 `<CLSCompliant(True)>` ，但根命名空間名稱的元素開頭為底線 (`_`) 。

 程式設計專案可以包含一或多個底線，但為了符合 Language-Independent 的 [語言獨立性和](../../../standard/language-independence-and-language-independent-components.md) (cls) 的元件，它不能以底線開頭。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。

 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。

 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC40039

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您需要 CLS 符合性，請變更根命名空間名稱，使其所有元素的開頭都不是底線。

- 如果您需要命名空間名稱保持不變，請 <xref:System.CLSCompliantAttribute> 從元件中移除，或將它標示為 `<CLSCompliant(False)>` 。

## <a name="see-also"></a>另請參閱

- [Namespace 陳述式](../statements/namespace-statement.md)
- [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../reference/command-line-compiler/rootnamespace.md)
- [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic 命名慣例](../../programming-guide/program-structure/naming-conventions.md)
