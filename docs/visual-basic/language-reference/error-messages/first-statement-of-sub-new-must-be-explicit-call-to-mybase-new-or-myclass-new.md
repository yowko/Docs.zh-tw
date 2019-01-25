---
title: 第一個陳述式，這個&#39;Sub New&#39;必須明確呼叫&#39;MyBase.New&#39;或&#39;MyClass.New&#39;因為&#39; &lt;constructorname&gt; &#39;基底類別中&#39;&lt;基&gt;&#39;的&#39;&lt;衍生類別名稱&gt;&#39;已標記為過時： &#39; &lt;errormessage&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9d07a68fd8d9790178427c512375323f23f46772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566766"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>第一個陳述式，這個&#39;Sub New&#39;必須明確呼叫&#39;MyBase.New&#39;或&#39;MyClass.New&#39;因為&#39; &lt;constructorname&gt; &#39;基底類別中&#39;&lt;基&gt;&#39;的&#39;&lt;衍生類別名稱&gt;&#39;已標記為過時： &#39; &lt;errormessage&gt;&#39;
類別建構函式未明確地呼叫基底類別建構函式，而且隱含的基底類別建構函式已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記，以將其視為錯誤。  
  
 當在衍生的類別建構函式未呼叫基底類別建構函式時，Visual Basic 會嘗試產生無參數的基底類別建構函式的隱含呼叫。 如果可以不使用引數呼叫的基底類別中沒有任何可存取建構函式，Visual Basic 無法產生隱含的呼叫。 在此情況下，需要的建構函式會以標記<xref:System.ObsoleteAttribute>屬性，讓 Visual Basic 無法呼叫它。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute> 。 如果您這麼做，則可以將屬性 (attribute) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 (property) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤 ID:** BC30920  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  包含 `MyBase.New()` 或 `MyClass.New()` 的呼叫作為衍生類別中 `Sub New` 的第一個陳述式。  
  
## <a name="see-also"></a>另請參閱
- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)

