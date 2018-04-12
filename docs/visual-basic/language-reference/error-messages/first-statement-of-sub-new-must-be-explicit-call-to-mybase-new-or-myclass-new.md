---
title: 這 &#39; 第一個陳述式新的子 &#39;必須明確呼叫 &#39;MyBase.New &#39;或 &#39;MyClass.New &#39;因為 &#39;&lt;constructorname&gt;&#39; 中的基底類別 &#39;&lt;基&gt;&#39; &#39;&lt;衍生類別名稱&gt;&#39; 已標記為過時： &#39;&lt;errormessage&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>這 &#39; 第一個陳述式新的子 &#39;必須明確呼叫 &#39;MyBase.New &#39;或 &#39;MyClass.New &#39;因為 &#39;&lt;constructorname&gt;&#39; 中的基底類別 &#39;&lt;基&gt;&#39; &#39;&lt;衍生類別名稱&gt;&#39; 已標記為過時： &#39;&lt;errormessage&gt;&#39;
類別建構函式未明確地呼叫基底類別建構函式，而且隱含的基底類別建構函式已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記，以將其視為錯誤。  
  
 當衍生類別建構函式未呼叫基底類別建構函式時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 會嘗試產生對無參數基底類別建構函式的隱含呼叫。 如果可以不使用引數呼叫的基底類別中沒有可存取的建構函式， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 就無法產生隱含的呼叫。 在這種情況下，會使用 <xref:System.ObsoleteAttribute> 屬性標記必要的建構函式，因此 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 無法呼叫它。  
  
 您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute> 。 如果您這麼做，則可以將屬性 (attribute) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 (property) 設定為 `True` 或 `False`。 如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。 如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。  
  
 **錯誤 ID:** BC30920  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，並採取適當的動作。  
  
2.  包含 `MyBase.New()` 或 `MyClass.New()` 的呼叫作為衍生類別中 `Sub New` 的第一個陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
