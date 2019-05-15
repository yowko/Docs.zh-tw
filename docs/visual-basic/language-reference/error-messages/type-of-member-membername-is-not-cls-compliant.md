---
title: 成員 '<membername>' 的類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590681"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a>成員的型別 '\<成員名稱 >' 不符合 CLS 標準
指定不是這個成員的資料類型的一部分[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準。 因為.NET Framework 和 Visual Basic 支援這種資料類型，這是不在您的元件中發生錯誤。 不過，另一個以完全符合 CLS 標準的程式碼撰寫的元件可能不支援這種資料類型。 這類元件可能無法順利與您的元件互動。  
  
 下列 Visual Basic 資料類型不符合 CLS 標準：  
  
- [SByte 資料類型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong 資料類型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort 資料類型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您的元件只能與其他.NET Framework 元件、 介面或不會與其他任何元件介面，則您不需要變更任何項目。  
  
- 如果您要使用的不是針對.NET Framework 撰寫的元件，您可能無法透過反映或文件，判斷是否支援此資料型別。 若是如此，您不需要變更任何項目。  
  
- 如果您要使用的元件不支援這種資料類型，您必須將它取代最符合 CLS 規範的型別。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
- 如果您要使用的 Automation 或 COM 物件，請記住，某些類型會有不同的資料寬度比在.NET Framework。 例如，`uint` 在其他環境中通常是 16 位元。 如果您將 16 位元引數傳遞給這類元件，將它宣告為`UShort`而不是`UInteger`中受管理的 Visual Basic 程式碼。  
  
## <a name="see-also"></a>另請參閱

- [反映](../../../framework/reflection-and-codedom/reflection.md)
