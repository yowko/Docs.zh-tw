---
title: "&lt;proceduresignature1&gt;不符合 CLS 標準，因為它多載&lt;proceduresignature2&gt;的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cdbd8edaefba4554e8de92cb600f045dc39f780
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt;不符合 CLS 標準，因為它多載&lt;proceduresignature2&gt;的差別只在於陣列參數類型的陣列，或是陣列參數類型的陣序規範
程序或屬性標示為`<CLSCompliant(True)>`時它會覆寫另一個程序或屬性和其參數清單中唯一的差別是巢狀的層級的不規則陣列陣序。  
  
 在下列宣告中，第二個和第三個宣告會產生此錯誤。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 第二個宣告會變更原始的一維參數`arrayParam`至陣列的陣列。 第三個宣告的變更`arrayParam`二維陣列 (rank 2)。 Visual Basic 可讓多載，可以僅由其中一個這些變更與不同，這類多載不符合[語言獨立性以及與語言無關的元件](../../../../docs/standard/language-independence-and-language-independent-components.md)（cls） 標準。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40035  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您需要 cls 符合性，定義您的多載，可以只將這個說明網頁所提到的變更的多種方式方面與彼此不同。  
  
-   如果您需要的多載的差別，只要在此說明所提到的變更頁面中，移除<xref:System.CLSCompliantAttribute>從其定義或將它們標記為`<CLSCompliant(False)>`。  
  
## <a name="see-also"></a>另請參閱  
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)  
 [程序多載化](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [多載](../../../visual-basic/language-reference/modifiers/overloads.md)
