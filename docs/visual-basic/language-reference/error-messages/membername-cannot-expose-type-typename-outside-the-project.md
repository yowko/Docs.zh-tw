---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397281"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="1a4bd-102">'\<membername>' 無法透過 \<typename> '\<containertype>' 在專案外部公開類型 '\<containertypename>'</span><span class="sxs-lookup"><span data-stu-id="1a4bd-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="1a4bd-103">變數、程式參數或函式傳回會在其容器外公開，但它會宣告為不能在容器外公開的類型。</span><span class="sxs-lookup"><span data-stu-id="1a4bd-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="1a4bd-104">下列基本架構程式碼會顯示產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="1a4bd-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="1a4bd-105">宣告為、、或的類型， `Protected` `Friend` `Protected Friend` `Private` 目的是要在其宣告內容之外擁有有限的存取權。</span><span class="sxs-lookup"><span data-stu-id="1a4bd-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="1a4bd-106">以較不受限制的存取來使用它做為變數的資料類型，將會破壞此目的。</span><span class="sxs-lookup"><span data-stu-id="1a4bd-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="1a4bd-107">在上述的基本架構程式碼中， `exposedVar` 是， `Public` 而且會公開 `privateClass` 給不應存取它的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a4bd-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="1a4bd-108">**錯誤識別碼：** BC30909</span><span class="sxs-lookup"><span data-stu-id="1a4bd-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a4bd-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1a4bd-109">To correct this error</span></span>  
  
- <span data-ttu-id="1a4bd-110">將變數、程式參數或函數傳回的存取層級變更為至少與其資料類型的存取層級相同。</span><span class="sxs-lookup"><span data-stu-id="1a4bd-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4bd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a4bd-111">See also</span></span>

- [<span data-ttu-id="1a4bd-112">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="1a4bd-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
