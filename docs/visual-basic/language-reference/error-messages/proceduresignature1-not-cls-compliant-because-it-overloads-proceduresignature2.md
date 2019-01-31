---
title: <proceduresignature1> 不符合 CLS 標準，因為它多載 <proceduresignature2>，而此兩者的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269558"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > 不符合 CLS 標準，因為它多載\<proceduresignature2 > 的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範
程序或屬性會標示為`<CLSCompliant(True)>`時它會覆寫另一個程序或屬性和其參數清單之間唯一的差別是巢狀層級的不規則陣列陣序。  
  
 在下列宣告中，第二個和第三個宣告會產生這個錯誤。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 第二個宣告會變更原始的一維參數`arrayParam`至陣列的陣列。 第三個宣告的變更`arrayParam`二維陣列 （也就是陣序 2）。 Visual Basic 可讓不同僅由其中一個這些變更的多載，這類多載與不相容[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40035  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您需要 cls 符合性，定義您的多載方面與彼此不同，在更多的方法，只將這個說明網頁所述的變更。  
  
-   如果您需要多載的差別只能由引用此說明的變更頁面上，移除<xref:System.CLSCompliantAttribute>從其定義或將它們標記為`<CLSCompliant(False)>`。  
  
## <a name="see-also"></a>另請參閱

- [程序多載化](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [多載](../../../visual-basic/language-reference/modifiers/overloads.md)
