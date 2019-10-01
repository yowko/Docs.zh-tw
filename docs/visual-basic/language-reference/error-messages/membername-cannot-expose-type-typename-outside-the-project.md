---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: ca67e74d7790352bd1842cb8a59fe1525af6e18c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700893"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="ec64e-102">' @no__t 0membername > ' 無法透過 \<containertype > ' \<containertypename > '，在專案外公開類型 ' \<typename > '</span><span class="sxs-lookup"><span data-stu-id="ec64e-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="ec64e-103">變數、程式參數或函式傳回會在其容器外公開，但它會宣告為不能在容器外公開的類型。</span><span class="sxs-lookup"><span data-stu-id="ec64e-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="ec64e-104">下列基本架構程式碼會顯示產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="ec64e-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="ec64e-105">@No__t-0、`Friend`、`Protected Friend` 或 `Private` 宣告的類型，主要是在其宣告內容外具有有限的存取權。</span><span class="sxs-lookup"><span data-stu-id="ec64e-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="ec64e-106">以較不受限制的存取來使用它做為變數的資料類型，將會破壞此目的。</span><span class="sxs-lookup"><span data-stu-id="ec64e-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="ec64e-107">在上述的基本架構程式碼中，`exposedVar` 會 `Public`，並將 `privateClass` 公開給不應該有存取權的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec64e-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="ec64e-108">**錯誤識別碼：** BC30909</span><span class="sxs-lookup"><span data-stu-id="ec64e-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec64e-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ec64e-109">To correct this error</span></span>  
  
- <span data-ttu-id="ec64e-110">將變數、程式參數或函數傳回的存取層級變更為至少與其資料類型的存取層級相同。</span><span class="sxs-lookup"><span data-stu-id="ec64e-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec64e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec64e-111">See also</span></span>

- [<span data-ttu-id="ec64e-112">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="ec64e-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
