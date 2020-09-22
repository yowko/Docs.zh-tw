---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 31d44c93d62163df4d81cb8503b633f0eb317372
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873803"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="3b7d0-102">'\<membername>' 無法透過 \<typename> '\<containertype>' 在專案外部公開類型 '\<containertypename>'</span><span class="sxs-lookup"><span data-stu-id="3b7d0-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>

<span data-ttu-id="3b7d0-103">變數、程式參數或函式傳回會在其容器之外公開，但會宣告為不能在容器外部公開的類型。</span><span class="sxs-lookup"><span data-stu-id="3b7d0-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="3b7d0-104">下列基本架構程式碼顯示會產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="3b7d0-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="3b7d0-105">宣告為、、或的型別， `Protected` `Friend` `Protected Friend` `Private` 目的是要在其宣告內容之外擁有有限的存取權。</span><span class="sxs-lookup"><span data-stu-id="3b7d0-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="3b7d0-106">將它當作限制存取權的變數資料類型，就會破壞這個目的。</span><span class="sxs-lookup"><span data-stu-id="3b7d0-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="3b7d0-107">在上述的基本架構程式碼中， `exposedVar` `Public` 和會公開 `privateClass` 至不應該有其存取權的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b7d0-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="3b7d0-108">**錯誤識別碼：** BC30909</span><span class="sxs-lookup"><span data-stu-id="3b7d0-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3b7d0-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3b7d0-109">To correct this error</span></span>  
  
- <span data-ttu-id="3b7d0-110">變更變數、程式參數或函式的存取層級，至少要與其資料類型的存取層級限制相同。</span><span class="sxs-lookup"><span data-stu-id="3b7d0-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7d0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b7d0-111">See also</span></span>

- [<span data-ttu-id="3b7d0-112">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="3b7d0-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
