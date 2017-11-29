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
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="fa3e4-102">使用 &#39;FilePutObject &#39;而不是 &#39;FilePut &#39;類型 &#39; 物件 &#39; 的引數時</span><span class="sxs-lookup"><span data-stu-id="fa3e4-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="fa3e4-103">`FilePut`方法包含類型的引數`Object`。</span><span class="sxs-lookup"><span data-stu-id="fa3e4-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="fa3e4-104">`FilePutObject` 應該用於取代 `FilePut` ，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="fa3e4-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa3e4-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fa3e4-105">To correct this error</span></span>  
  
-   <span data-ttu-id="fa3e4-106">將 `FilePut` 取代為 `FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="fa3e4-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="fa3e4-107">請將 `Object` 引數轉換為更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="fa3e4-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="fa3e4-108">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="fa3e4-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3e4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa3e4-109">See Also</span></span>  
 [<span data-ttu-id="fa3e4-110">不在組建中： FilePutObject 函式</span><span class="sxs-lookup"><span data-stu-id="fa3e4-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="fa3e4-111">My.Computer.FileSystem 物件</span><span class="sxs-lookup"><span data-stu-id="fa3e4-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="fa3e4-112">My.Computer.FileSystem.WriteAllBytes 方法</span><span class="sxs-lookup"><span data-stu-id="fa3e4-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
