---
title: "這個 &quot;Sub New&quot; 的第一個陳述式必須明確呼叫 &quot;MyBase.New&quot; 或 &quot;MyClass.New&quot;，因為&quot;&lt;constructorname&gt;&quot;中的基底類別&quot;&lt;baseclassname&gt;&quot;的&quot;&lt;derivedclassname&gt;&quot;標記為過時:&quot;&lt;errormessage&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
dev_langs:
- VB
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
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
ms.openlocfilehash: feb04d426b7e050b7ad05cdfd4d481172dda3a49
ms.lasthandoff: 03/13/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>這個 'Sub New' 的第一個陳述式必須明確呼叫 'MyBase.New' 或 'MyClass.New'，因為'&lt;constructorname&gt;'中的基底類別'&lt;baseclassname&gt;'的'&lt;derivedclassname&gt;'標記為過時:'&lt;errormessage&gt;'
類別建構函式不會明確地呼叫基底類別建構函式，並會加上隱含基底類別建構函式<xref:System.ObsoleteAttribute>屬性並將其視為錯誤的指示詞。</xref:System.ObsoleteAttribute>  
  
 當在衍生的類別建構函式未呼叫基底類別建構函式，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會嘗試產生無參數的基底類別建構函式的隱含呼叫。 如果沒有引數，就無法呼叫基底類別中沒有可存取建構函式[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不會產生隱含呼叫。 在此情況下，必要的建構函式會標示<xref:System.ObsoleteAttribute>屬性，因此[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法呼叫它。</xref:System.ObsoleteAttribute>  
  
 您可以將標記為不再使用<xref:System.ObsoleteAttribute>該</xref:System.ObsoleteAttribute>套用任何程式設計項目 如果您這麼做，您可以設定屬性的<xref:System.ObsoleteAttribute.IsError%2A>屬性設為`True`或`False`。</xref:System.ObsoleteAttribute.IsError%2A> 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤識別碼︰** BC30920  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  包含 `MyBase.New()` 或 `MyClass.New()` 的呼叫作為衍生類別中 `Sub New` 的第一個陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
