---
title: 使用&#39;FileGetObject&#39;而不是&#39;FileGet&#39;的型別引數時&#39;物件&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640413"
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="b5f58-102">使用&#39;FileGetObject&#39;而不是&#39;FileGet&#39;的型別引數時&#39;物件&#39;</span><span class="sxs-lookup"><span data-stu-id="b5f58-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="b5f58-103">`FileGet` 方法包含類型 `Object`的引數。</span><span class="sxs-lookup"><span data-stu-id="b5f58-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="b5f58-104">`FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="b5f58-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="b5f58-105">請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。</span><span class="sxs-lookup"><span data-stu-id="b5f58-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5f58-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b5f58-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b5f58-107">將 `FileGet` 取代為 `FileGetObject`。</span><span class="sxs-lookup"><span data-stu-id="b5f58-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="b5f58-108">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="b5f58-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f58-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5f58-109">See Also</span></span>  
   
 [<span data-ttu-id="b5f58-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="b5f58-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
