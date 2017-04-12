---
title: "&lt;proceduresignature1&gt;不符合 CLS 標準，因為它多載&lt;proceduresignature2&gt;的差別只在於陣列參數型別的陣列，或是陣列參數類型的陣序規範 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
dev_langs:
- VB
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 984c04a107444036b980439b231d27a8a81656c1
ms.lasthandoff: 03/13/2017

---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt;不符合 CLS 標準，因為它多載&lt;proceduresignature2&gt;的差別只在於陣列參數型別的陣列，或是陣列參數類型的陣序規範
程序或屬性會標示為`<CLSCompliant(True)>`時它會覆寫另一個程序或屬性和其參數清單的唯一差別是巢狀的層級的不規則陣列的陣序規範。  
  
 在下列宣告，第二個和第三個宣告會產生此錯誤。  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 第二個宣告變更原始的一維參數`arrayParam`至陣列的陣列。 第三個宣告的變更`arrayParam`二維陣列 (rank 2)。 Visual Basic 可讓多載，可以僅由其中一個這些變更會與不同，這類多載不符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)。  
  
 當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute> 這個參數沒有預設值，您必須提供值。  
  
 如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40035  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如需 cls 符合性，定義您的多載，不同於其他多種方式比只引用這個說明網頁上的變更。  
  
-   如果您需要的多載的差別只能由引用此說明的變更 頁面上，移除<xref:System.CLSCompliantAttribute>其定義或將它們標記為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>另請參閱  
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [多載化程序](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [多載](../../../visual-basic/language-reference/modifiers/overloads.md)
