---
title: 使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 318a0772a99aa86d9a4633e6021f77616a43fc7e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059401"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="ae46a-102">使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'</span><span class="sxs-lookup"><span data-stu-id="ae46a-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>

<span data-ttu-id="ae46a-103">`FileGet` 方法包含類型 `Object`的引數。</span><span class="sxs-lookup"><span data-stu-id="ae46a-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="ae46a-104">`FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="ae46a-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="ae46a-105">請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。</span><span class="sxs-lookup"><span data-stu-id="ae46a-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ae46a-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ae46a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="ae46a-107">將 `FileGet` 取代為 `FileGetObject`。</span><span class="sxs-lookup"><span data-stu-id="ae46a-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="ae46a-108">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="ae46a-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae46a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae46a-109">See also</span></span>

- [<span data-ttu-id="ae46a-110">我的電腦. 檔案系統</span><span class="sxs-lookup"><span data-stu-id="ae46a-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
