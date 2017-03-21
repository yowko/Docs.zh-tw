---
title: "非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
dev_langs:
- VB
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 2861ef22c9307e5bd7d2eabf4f6e37bbd9086345
ms.lasthandoff: 03/13/2017

---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>非 CLS 相容&lt;membername&gt;符合 CLS 標準的介面中不允許
屬性、 程序或事件的介面中標示為`<CLSCompliant(True)>`介面本身會標示為`<CLSCompliant(False)>`或未標記。  
  
 為了符合介面[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，其所有成員都必須相容。  
  
 當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute> 這個參數沒有預設值，您必須提供值。  
  
 如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40033  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您需要將 cls 符合性，而且介面原始程式碼控制，將介面標記為`<CLSCompliant(True)>`如果其所有成員都都相容。  
  
-   如果需要將 cls 符合性，而且不需要控制介面的原始碼，或它不會不符合 cls 標準，定義此成員內不同的介面。  
  
-   如果您需要這個成員會維持其目前的介面中，移除<xref:System.CLSCompliantAttribute>從其定義或標示為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>另請參閱  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
