---
title: 參數 '<parametername>' 的類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: 7043138f770264b73eeac79cd262104b88cd8516
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161227"
---
# <a name="bc40028-type-of-parameter-parametername-is-not-cls-compliant"></a>BC40028：參數 ' ' 的類型 \<parametername> 不符合 CLS 規範

程式標示為 `<CLSCompliant(True)>` ，但宣告的參數具有標記為的類型、未標記，或是不符合規範， `<CLSCompliant(False)>` 因為它是不相容的類型。

 程序必須只使用符合 CLS 標準的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。 這適用於參數型別、傳回型別及其所有區域變數的型別。

 下列 Visual Basic 資料類型不符合 CLS 規範：

- [SByte 資料類型](../data-types/sbyte-data-type.md)

- [UInteger 資料類型](../data-types/uinteger-data-type.md)

- [ULong 資料類型](../data-types/ulong-data-type.md)

- [UShort 資料類型](../data-types/ushort-data-type.md)

 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。

 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC40028

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果程式必須採用此特定類型的參數，請移除 <xref:System.CLSCompliantAttribute> 。 程序不符合 CLS 標準。

- 如果程式必須符合 CLS 規範，請將此參數的類型變更為最符合 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。

- 如果您要與 Automation 或 COM 物件互動，請記住，有些類型的資料寬度會與 .NET Framework 中的資料寬度不同。 例如，`int` 在其他環境中通常是 16 位元。 如果您接受來自這類元件的16位整數，請 `Short` `Integer` 在您的 managed Visual Basic 程式碼中將它宣告為，而不是。
