---
title: "'<membername>' 無法透過 <typename> '<containertype>' 在專案外部公開類型 '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: cb5191442ed8d3ee47c5116b10740e277ffa5bac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661920"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="ec926-102">'\<成員名稱 >' 無法公開類型'\<類型名稱 >' 透過在專案外\<containertype > '\<containertypename >'</span><span class="sxs-lookup"><span data-stu-id="ec926-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="ec926-103">變數、 程序參數或函式傳回外部公開其容器，但它卻宣告為不會公開對容器外部的型別。</span><span class="sxs-lookup"><span data-stu-id="ec926-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="ec926-104">下列的基本架構程式碼顯示會產生此錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="ec926-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="ec926-105">宣告的型別`Protected`， `Friend`， `Protected Friend`，或`Private`旨在有限存取，其宣告的內容之外。</span><span class="sxs-lookup"><span data-stu-id="ec926-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="ec926-106">使用做為資料類型的限制較少存取的變數會破壞此目的。</span><span class="sxs-lookup"><span data-stu-id="ec926-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="ec926-107">在上述的基本架構程式碼中，`exposedVar`是`Public`，並會公開`privateClass`不應該存取它的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec926-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="ec926-108">**錯誤 ID:** BC30909</span><span class="sxs-lookup"><span data-stu-id="ec926-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec926-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ec926-109">To correct this error</span></span>  
  
- <span data-ttu-id="ec926-110">變更存取層級的變數、 程序參數或函式會傳回至少為其資料類型的存取層級限制。</span><span class="sxs-lookup"><span data-stu-id="ec926-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec926-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec926-111">See also</span></span>

- [<span data-ttu-id="ec926-112">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="ec926-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
