---
title: "使用 &#39;FilePutObject &#39;而不是 &#39;FilePut &#39;類型 &#39; 物件 &#39; 的引數時"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="d5659-102">使用 &#39;FilePutObject &#39;而不是 &#39;FilePut &#39;類型 &#39; 物件 &#39; 的引數時</span><span class="sxs-lookup"><span data-stu-id="d5659-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="d5659-103">`FilePut`方法包含類型的引數`Object`。</span><span class="sxs-lookup"><span data-stu-id="d5659-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="d5659-104">`FilePutObject` 應該用於取代 `FilePut` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="d5659-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5659-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d5659-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d5659-106">將 `FilePut` 取代為 `FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="d5659-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="d5659-107">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="d5659-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="d5659-108">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="d5659-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5659-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5659-109">See Also</span></span>  
   
 [<span data-ttu-id="d5659-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="d5659-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="d5659-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="d5659-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
