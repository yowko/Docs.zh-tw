---
title: "名稱&lt;membername&gt;不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: 9
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
ms.openlocfilehash: 6a678c66580a7917a3869aac81418152130debff
ms.lasthandoff: 03/13/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>名稱&lt;membername&gt;不符合 CLS 標準
組件標示為`<CLSCompliant(True)>`但公開成員的名稱開頭為底線 (`_`)。  
  
 程式設計項目可以包含一或多個底線，但要遵守[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，它必須未以底線開頭。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute> 這個參數沒有預設值，您必須提供值。  
  
 如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40031  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您有原始程式碼控制，變更成員名稱，使它不是以底線開頭。  
  
-   如果您需要的成員名稱保持不變，移除<xref:System.CLSCompliantAttribute>從其定義或標示為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute> 您仍然可以將標記的組件`<CLSCompliant(True)>`。  
  
## <a name="see-also"></a>另請參閱  
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
