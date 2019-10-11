---
title: 因為 <proceduresignature1> 多載了<proceduresignature2>，不同於只在於陣列參數類型的陣列，或是陣列參數類型的順位，所以不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250174"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>@no__t 0proceduresignature1 > 不符合 CLS 規範，因為它會多載 @no__t 1proceduresignature2 的 >，而這與只有陣列參數類型的陣列或陣列參數類型的順位不同

程式或屬性會在覆寫另一個程式或屬性時標示為 `<CLSCompliant(True)>`，而且其參數清單之間的唯一差異是不規則陣列的嵌套層級或陣列的次序。
  
 在下列宣告中，第二個和第三個宣告會產生此錯誤：
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 第二個宣告會將原始的一維參數 `arrayParam` 變更為陣列陣列。 第三個宣告會將 `arrayParam` 變更為二維陣列（順位2）。 雖然 Visual Basic 只允許多載不同于這些變更的其中一個，但這類超載並不符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC40035  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您需要 CLS 合規性，請將您的多載定義成不同于此說明頁面上所述之變更的方式。
- 如果您要求多載只因此說明頁面上所述的變更而不同，請從其定義中移除 <xref:System.CLSCompliantAttribute>，或將它們標示為 `<CLSCompliant(False)>`。
  
## <a name="see-also"></a>另請參閱

- [程序多載化](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [多載](../modifiers/overloads.md)
