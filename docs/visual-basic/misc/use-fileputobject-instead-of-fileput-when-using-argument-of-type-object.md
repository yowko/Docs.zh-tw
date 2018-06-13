---
title: 使用&#39;FilePutObject&#39;而不是&#39;FilePut&#39;的型別引數時&#39;物件&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641124"
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="05171-102">使用&#39;FilePutObject&#39;而不是&#39;FilePut&#39;的型別引數時&#39;物件&#39;</span><span class="sxs-lookup"><span data-stu-id="05171-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="05171-103">`FilePut`方法包含類型的引數`Object`。</span><span class="sxs-lookup"><span data-stu-id="05171-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="05171-104">`FilePutObject` 應該用於取代 `FilePut` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="05171-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05171-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="05171-105">To correct this error</span></span>  
  
-   <span data-ttu-id="05171-106">將 `FilePut` 取代為 `FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="05171-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="05171-107">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="05171-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="05171-108">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="05171-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05171-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05171-109">See Also</span></span>  
   
 [<span data-ttu-id="05171-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="05171-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="05171-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="05171-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
