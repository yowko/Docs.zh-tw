---
title: "封送處理字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 750f4e6852cd5aa52d03f884edcbfbf80ed5fab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-strings"></a><span data-ttu-id="49f57-102">封送處理字串</span><span class="sxs-lookup"><span data-stu-id="49f57-102">Marshaling Strings</span></span>
<span data-ttu-id="49f57-103">平台叫用會複製字串參數，並視需要從 .NET Framework 格式 (Unicode) 轉換成 Unmanaged 格式 (ANSI)。</span><span class="sxs-lookup"><span data-stu-id="49f57-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="49f57-104">傳回函式時，因為 Managed 字串不可變，所以平台叫用不會將 Managed 字串從 Unmanaged 記憶體複製回 Managed 記憶體。</span><span class="sxs-lookup"><span data-stu-id="49f57-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="49f57-105">下表列出字串的封送處理選項，並描述其用法，以及提供對應 .NET Framework 範例的連結。</span><span class="sxs-lookup"><span data-stu-id="49f57-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="49f57-106">String</span><span class="sxs-lookup"><span data-stu-id="49f57-106">String</span></span>|<span data-ttu-id="49f57-107">描述</span><span class="sxs-lookup"><span data-stu-id="49f57-107">Description</span></span>|<span data-ttu-id="49f57-108">範例</span><span class="sxs-lookup"><span data-stu-id="49f57-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="49f57-109">傳值。</span><span class="sxs-lookup"><span data-stu-id="49f57-109">By value.</span></span>|<span data-ttu-id="49f57-110">將字串傳遞為 In 參數。</span><span class="sxs-lookup"><span data-stu-id="49f57-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="49f57-111">MsgBox</span><span class="sxs-lookup"><span data-stu-id="49f57-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="49f57-112">作為結果。</span><span class="sxs-lookup"><span data-stu-id="49f57-112">As result.</span></span>|<span data-ttu-id="49f57-113">從 Unmanaged 程式碼傳回字串。</span><span class="sxs-lookup"><span data-stu-id="49f57-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="49f57-114">字串</span><span class="sxs-lookup"><span data-stu-id="49f57-114">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="49f57-115">傳址。</span><span class="sxs-lookup"><span data-stu-id="49f57-115">By reference.</span></span>|<span data-ttu-id="49f57-116">使用 <xref:System.Text.StringBuilder> 將字串傳遞為 In/Out 參數。</span><span class="sxs-lookup"><span data-stu-id="49f57-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="49f57-117">緩衝區</span><span class="sxs-lookup"><span data-stu-id="49f57-117">Buffers</span></span>](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="49f57-118">在傳值結構中。</span><span class="sxs-lookup"><span data-stu-id="49f57-118">In a structure by value.</span></span>|<span data-ttu-id="49f57-119">透過本身為 In 參數的結構傳遞字串。</span><span class="sxs-lookup"><span data-stu-id="49f57-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="49f57-120">結構</span><span class="sxs-lookup"><span data-stu-id="49f57-120">Structs</span></span>](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="49f57-121">在傳址結構中 **(char\*)**。</span><span class="sxs-lookup"><span data-stu-id="49f57-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="49f57-122">透過本身為 In/Out 參數的結構傳遞字串。</span><span class="sxs-lookup"><span data-stu-id="49f57-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="49f57-123">Unmanaged 函式需要字元緩衝區的指標，而且緩衝區大小是結構的成員。</span><span class="sxs-lookup"><span data-stu-id="49f57-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="49f57-124">字串</span><span class="sxs-lookup"><span data-stu-id="49f57-124">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="49f57-125">在傳址結構中 **(char[])**。</span><span class="sxs-lookup"><span data-stu-id="49f57-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="49f57-126">透過本身為 In/Out 參數的結構傳遞字串。</span><span class="sxs-lookup"><span data-stu-id="49f57-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="49f57-127">Unmanaged 函式需要內嵌的字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="49f57-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="49f57-128">OSInfo</span><span class="sxs-lookup"><span data-stu-id="49f57-128">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="49f57-129">在傳值類別中 **(char\*)**。</span><span class="sxs-lookup"><span data-stu-id="49f57-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="49f57-130">在類別中傳遞字串 (類別是 In/Out 參數)。</span><span class="sxs-lookup"><span data-stu-id="49f57-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="49f57-131">Unmanaged 函式需要字元緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="49f57-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="49f57-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="49f57-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="49f57-133">在傳值類別中 **(char[])**。</span><span class="sxs-lookup"><span data-stu-id="49f57-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="49f57-134">在類別中傳遞字串 (類別是 In/Out 參數)。</span><span class="sxs-lookup"><span data-stu-id="49f57-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="49f57-135">Unmanaged 函式需要內嵌的字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="49f57-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="49f57-136">OSInfo</span><span class="sxs-lookup"><span data-stu-id="49f57-136">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="49f57-137">作為傳值字串陣列。</span><span class="sxs-lookup"><span data-stu-id="49f57-137">As an array of strings by value.</span></span>|<span data-ttu-id="49f57-138">建立以傳值方式傳遞的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="49f57-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="49f57-139">陣列</span><span class="sxs-lookup"><span data-stu-id="49f57-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="49f57-140">作為包含傳值字串的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="49f57-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="49f57-141">建立包含字串的結構陣列，並以傳值方式傳遞該陣列。</span><span class="sxs-lookup"><span data-stu-id="49f57-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="49f57-142">陣列</span><span class="sxs-lookup"><span data-stu-id="49f57-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="49f57-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49f57-143">See Also</span></span>  
 [<span data-ttu-id="49f57-144">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="49f57-144">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="49f57-145">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="49f57-145">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="49f57-146">封送處理類別、結構和等位</span><span class="sxs-lookup"><span data-stu-id="49f57-146">Marshaling Classes, Structures, and Unions</span></span>](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [<span data-ttu-id="49f57-147">封送處理類型的陣列</span><span class="sxs-lookup"><span data-stu-id="49f57-147">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="49f57-148">其他封送處理範例</span><span class="sxs-lookup"><span data-stu-id="49f57-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
