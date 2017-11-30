---
title: "使用 &#39;FileGetObject &#39;而不是 &#39;FileGet &#39;類型 &#39; 物件 &#39; 的引數時"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="a7e7a-102">使用 &#39;FileGetObject &#39;而不是 &#39;FileGet &#39;類型 &#39; 物件 &#39; 的引數時</span><span class="sxs-lookup"><span data-stu-id="a7e7a-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="a7e7a-103">`FileGet` 方法包含類型 `Object`的引數。</span><span class="sxs-lookup"><span data-stu-id="a7e7a-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="a7e7a-104">`FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="a7e7a-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="a7e7a-105">請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。</span><span class="sxs-lookup"><span data-stu-id="a7e7a-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7e7a-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a7e7a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a7e7a-107">將 `FileGet` 取代為 `FileGetObject`。</span><span class="sxs-lookup"><span data-stu-id="a7e7a-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="a7e7a-108">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="a7e7a-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e7a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7e7a-109">See Also</span></span>  
 [<span data-ttu-id="a7e7a-110">不在組建中： FileGetObject 函式</span><span class="sxs-lookup"><span data-stu-id="a7e7a-110">NOT IN BUILD: FileGetObject Function</span></span>](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [<span data-ttu-id="a7e7a-111">My.Computer.FileSystem 物件</span><span class="sxs-lookup"><span data-stu-id="a7e7a-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
