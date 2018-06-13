---
title: 名稱&lt;membername&gt;不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 26ff13de461d5a96724868b7928129a326cdf1d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593337"
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>名稱&lt;membername&gt;不符合 CLS 標準
組件標示為`<CLSCompliant(True)>`但公開的成員名稱開頭為底線 (`_`)。  
  
 程式設計項目可以包含一或多個底線，但若要遵守[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準，它必須不以底線開頭。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40031  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您有原始程式碼控制，變更成員名稱，使它不是以底線開頭。  
  
-   如果您需要的成員名稱維持不變，移除<xref:System.CLSCompliantAttribute>從其定義或將其標記為`<CLSCompliant(False)>`。 您仍可以標示為組件`<CLSCompliant(True)>`。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  

