---
title: 列舉的基礎類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 42c2398945b97d68161af6fb3c3b69909f4aaf39
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161513"
---
# <a name="bc40032-underlying-type-typename-of-enum-is-not-cls-compliant"></a>BC40032： \<typename> 列舉的基礎類型不符合 CLS 規範

針對此列舉指定的資料類型不是 [語言獨立性的一部分，而](../../../standard/language-independence-and-language-independent-components.md) 是 (CLS) 的 Language-Independent 元件。 這不是您的元件內的錯誤，因為 .NET Framework 和 Visual Basic 支援此資料類型。 不過，以嚴格符合 CLS 標準的程式碼撰寫的另一個元件可能不支援此資料類型。 這類元件可能無法成功與您的元件互動。

 下列 Visual Basic 資料類型不符合 CLS 規範：

- [SByte 資料類型](../data-types/sbyte-data-type.md)

- [UInteger 資料類型](../data-types/uinteger-data-type.md)

- [ULong 資料類型](../data-types/ulong-data-type.md)

- [UShort 資料類型](../data-types/ushort-data-type.md)

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC40032

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您的元件僅與其他 .NET Framework 元件互動，或未與任何其他元件互動，您就不需要變更任何動作。

- 如果您要與未針對 .NET Framework 撰寫的元件進行互動，您可以透過反映或從檔中判斷是否支援此資料類型。 如果有，您就不需要變更任何變更。

- 如果您要與不支援此資料類型的元件互動，您必須將它取代為最符合 CLS 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。

- 如果您要與 Automation 或 COM 物件互動，請記住，有些類型的資料寬度會與 .NET Framework 中的資料寬度不同。 例如，`uint` 在其他環境中通常是 16 位元。 如果您要將16位引數傳遞至這類元件，請 `UShort` `UInteger` 在您的 managed Visual Basic 程式碼中將它宣告為，而不是。

## <a name="see-also"></a>另請參閱

- [反映 (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [反射](../../../framework/reflection-and-codedom/reflection.md)
