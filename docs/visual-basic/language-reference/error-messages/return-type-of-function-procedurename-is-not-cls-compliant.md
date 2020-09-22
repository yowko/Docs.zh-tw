---
title: 函式 '<procedurename>' 的傳回類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 8ced0b6e06edadd9aed787aab2e715a2853e73a9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870838"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a>函式 '\<procedurename>' 的傳回類型不符合 CLS 標準

程式 `Function` 標示為 `<CLSCompliant(True)>` ，但會傳回標示為、未標記或不合格的類型， `<CLSCompliant(False)>` 因為它是不相容的類型。  
  
 程序必須只使用符合 CLS 標準的型別，才能夠符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 標準。 這適用於參數型別、傳回型別及其所有區域變數的型別。  
  
 下列 Visual Basic 資料類型不符合 CLS 規範：  
  
- [SByte 資料類型](../data-types/sbyte-data-type.md)  
  
- [UInteger 資料類型](../data-types/uinteger-data-type.md)  
  
- [ULong 資料類型](../data-types/ulong-data-type.md)  
  
- [UShort 資料類型](../data-types/ushort-data-type.md)  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC40027  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果程式 `Function` 必須傳回此特定類型，請移除 <xref:System.CLSCompliantAttribute> 。 程序不符合 CLS 標準。  
  
- 如果程式 `Function` 必須符合 cls 規範，請將傳回類型變更為最符合 cls 標準的類型。 例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。 如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。  
  
- 如果您要與 Automation 或 COM 物件互動，請記住，有些類型的資料寬度會與 .NET Framework 中的資料寬度不同。 例如，`int` 在其他環境中通常是 16 位元。 如果您要將16位整數傳回給這類元件，請 `Short` `Integer` 在您的 managed Visual Basic 程式碼中將它宣告為，而不是。
