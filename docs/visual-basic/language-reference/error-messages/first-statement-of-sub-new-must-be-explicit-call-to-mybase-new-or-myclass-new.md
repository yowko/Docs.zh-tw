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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d46192bc9a9f2807f56cbdd7bdd4fd21f6c9a7b0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="99524-102">這個 'Sub New' 的第一個陳述式必須明確呼叫 'MyBase.New' 或 'MyClass.New'，因為'&lt;constructorname&gt;'中的基底類別'&lt;baseclassname&gt;'的'&lt;derivedclassname&gt;'標記為過時:'&lt;errormessage&gt;'</span><span class="sxs-lookup"><span data-stu-id="99524-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="99524-103">類別建構函式不會明確地呼叫基底類別建構函式，並會加上隱含基底類別建構函式<xref:System.ObsoleteAttribute>屬性並將其視為錯誤的指示詞。</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="99524-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="99524-104">當在衍生的類別建構函式未呼叫基底類別建構函式，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會嘗試產生無參數的基底類別建構函式的隱含呼叫。</span><span class="sxs-lookup"><span data-stu-id="99524-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="99524-105">如果沒有引數，就無法呼叫基底類別中沒有可存取建構函式[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不會產生隱含呼叫。</span><span class="sxs-lookup"><span data-stu-id="99524-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="99524-106">在此情況下，必要的建構函式會標示<xref:System.ObsoleteAttribute>屬性，因此[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法呼叫它。</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="99524-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="99524-107">您可以將標記為不再使用<xref:System.ObsoleteAttribute>該</xref:System.ObsoleteAttribute>套用任何程式設計項目</span><span class="sxs-lookup"><span data-stu-id="99524-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="99524-108">如果您這麼做，您可以設定屬性的<xref:System.ObsoleteAttribute.IsError%2A>屬性設為`True`或`False`。</xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="99524-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="99524-109">如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="99524-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="99524-110">如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="99524-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="99524-111">**錯誤識別碼︰** BC30920</span><span class="sxs-lookup"><span data-stu-id="99524-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="99524-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="99524-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="99524-113">請檢查引用的錯誤訊息，並採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="99524-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="99524-114">包含 `MyBase.New()` 或 `MyClass.New()` 的呼叫作為衍生類別中 `Sub New` 的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="99524-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99524-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99524-115">See Also</span></span>  
 [<span data-ttu-id="99524-116">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="99524-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
