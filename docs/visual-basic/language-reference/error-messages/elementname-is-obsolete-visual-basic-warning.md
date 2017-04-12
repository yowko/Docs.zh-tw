---
title: "&quot;&lt;elementname&gt;&quot; 已過時 （Visual Basic 警告） |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
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
ms.openlocfilehash: ccec3b2659502c84dd4db9c9c4d796362958030b
ms.lasthandoff: 03/13/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>'&lt;elementname&gt;' 已過時 （Visual Basic 警告）
陳述式嘗試存取程式設計的項目被標示與<xref:System.ObsoleteAttribute>屬性並將其視為警告指示詞。</xref:System.ObsoleteAttribute>  
  
 您可以將標記為不再使用<xref:System.ObsoleteAttribute>該</xref:System.ObsoleteAttribute>套用任何程式設計項目 如果您這麼做，您可以設定屬性的<xref:System.ObsoleteAttribute.IsError%2A>屬性設為`True`或`False`。</xref:System.ObsoleteAttribute.IsError%2A> 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 根據預設，這是一個警告訊息，因為<xref:System.ObsoleteAttribute.IsError%2A>屬性<xref:System.ObsoleteAttribute>是`False`。</xref:System.ObsoleteAttribute> </xref:System.ObsoleteAttribute.IsError%2A> 如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40008  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定原始程式碼參考正確拼寫項目名稱。  
  
## <a name="see-also"></a>另請參閱  
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)

