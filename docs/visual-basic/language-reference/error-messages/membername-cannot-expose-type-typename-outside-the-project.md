---
title: '&#39;&lt;membername&gt; &#39;無法公開型別&#39; &lt;typename&gt; &#39;透過在專案外&lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="d97d3-102">&#39;&lt;membername&gt; &#39;無法公開型別&#39; &lt;typename&gt; &#39;透過在專案外&lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="d97d3-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="d97d3-103">變數、 程序參數或函式傳回其容器，外部公開，但它卻宣告為不會公開容器外的型別。</span><span class="sxs-lookup"><span data-stu-id="d97d3-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="d97d3-104">下列的基本架構程式碼將示範會產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="d97d3-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="d97d3-105">宣告的型別`Protected`， `Friend`， `Protected Friend`，或`Private`要擁有受限存取其宣告的內容之外。</span><span class="sxs-lookup"><span data-stu-id="d97d3-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="d97d3-106">使用的資料類型的限制較少存取的變數會破壞此用途。</span><span class="sxs-lookup"><span data-stu-id="d97d3-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="d97d3-107">在上述的基本架構程式碼，`exposedVar`是`Public`和會公開`privateClass`不應該有其存取權的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d97d3-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="d97d3-108">**錯誤 ID:** BC30909</span><span class="sxs-lookup"><span data-stu-id="d97d3-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d97d3-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d97d3-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d97d3-110">變更變數、 程序參數或函式的存取層級會傳回至少嚴格愈好其資料類型的存取層級。</span><span class="sxs-lookup"><span data-stu-id="d97d3-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97d3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d97d3-111">See Also</span></span>  
 [<span data-ttu-id="d97d3-112">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="d97d3-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
