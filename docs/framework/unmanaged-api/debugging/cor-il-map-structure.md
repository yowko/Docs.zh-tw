---
title: "COR_IL_MAP 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_IL_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_IL_MAP
helpviewer_keywords: COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffcd4dc32f2f509dd9421b2c24781fb2819418b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corilmap-structure"></a><span data-ttu-id="ce69a-102">COR_IL_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="ce69a-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="ce69a-103">指定函式相關位移中的變更。</span><span class="sxs-lookup"><span data-stu-id="ce69a-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce69a-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce69a-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="ce69a-105">成員</span><span class="sxs-lookup"><span data-stu-id="ce69a-105">Members</span></span>  
  
|<span data-ttu-id="ce69a-106">成員</span><span class="sxs-lookup"><span data-stu-id="ce69a-106">Member</span></span>|<span data-ttu-id="ce69a-107">說明</span><span class="sxs-lookup"><span data-stu-id="ce69a-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="ce69a-108">舊 Microsoft 中繼語言 (MSIL) 位移相對於函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="ce69a-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="ce69a-109">新的 MSIL 位移相對於函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="ce69a-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="ce69a-110">`true`如果對應是否已知為精確;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="ce69a-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce69a-111">備註</span><span class="sxs-lookup"><span data-stu-id="ce69a-111">Remarks</span></span>  
 <span data-ttu-id="ce69a-112">對應的格式如下所示： 偵錯工具會假設`oldOffset`指的是在原始、 未修改 MSIL 程式碼的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="ce69a-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="ce69a-113">`newOffset`參數是指在新的已檢測的程式碼中對應的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="ce69a-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="ce69a-114">逐步執行才能正常運作，應該符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="ce69a-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="ce69a-115">此對應應該以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="ce69a-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="ce69a-116">已檢測的 MSIL 程式碼不應該重新排列。</span><span class="sxs-lookup"><span data-stu-id="ce69a-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="ce69a-117">不應該移除原始的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce69a-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="ce69a-118">此對應應該包含對應程式資料庫 (PDB) 檔案中的所有序列點的項目。</span><span class="sxs-lookup"><span data-stu-id="ce69a-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="ce69a-119">對應不會不進行插補遺漏的項目。</span><span class="sxs-lookup"><span data-stu-id="ce69a-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="ce69a-120">下列範例顯示的地圖與它的結果。</span><span class="sxs-lookup"><span data-stu-id="ce69a-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="ce69a-121">對應：</span><span class="sxs-lookup"><span data-stu-id="ce69a-121">Map:</span></span>  
  
-   <span data-ttu-id="ce69a-122">舊的位移 0，0 新位移</span><span class="sxs-lookup"><span data-stu-id="ce69a-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="ce69a-123">舊的位移 5、 10 個新的位移</span><span class="sxs-lookup"><span data-stu-id="ce69a-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="ce69a-124">舊的位移 9、 20 新位移</span><span class="sxs-lookup"><span data-stu-id="ce69a-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="ce69a-125">結果：</span><span class="sxs-lookup"><span data-stu-id="ce69a-125">Results:</span></span>  
  
-   <span data-ttu-id="ce69a-126">0、 1、 2、 3 或 4 的舊位移會對應為新的位移為 0。</span><span class="sxs-lookup"><span data-stu-id="ce69a-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="ce69a-127">5、 6、 7 或 8 的舊位移會對應至新的位移 10。</span><span class="sxs-lookup"><span data-stu-id="ce69a-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="ce69a-128">9 或更高版本的舊位移會對應至新的位移 20。</span><span class="sxs-lookup"><span data-stu-id="ce69a-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="ce69a-129">0、 1、 2、 3、 4、 5、 6、 7、 8 或 9 的新位移會對應至舊的位移 0。</span><span class="sxs-lookup"><span data-stu-id="ce69a-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="ce69a-130">為新的位移 10、 11、 12、 13、 14、 15、 16、 17、 18 或 19 的會對應至舊的位移 5。</span><span class="sxs-lookup"><span data-stu-id="ce69a-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="ce69a-131">20 或更高版本的新位移會對應至舊的位移 9。</span><span class="sxs-lookup"><span data-stu-id="ce69a-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce69a-132">需求</span><span class="sxs-lookup"><span data-stu-id="ce69a-132">Requirements</span></span>  
 <span data-ttu-id="ce69a-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce69a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce69a-134">**標頭：** CorDebug.idl、 CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ce69a-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="ce69a-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce69a-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce69a-136">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce69a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce69a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce69a-137">See Also</span></span>  
 [<span data-ttu-id="ce69a-138">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="ce69a-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ce69a-139">偵錯</span><span class="sxs-lookup"><span data-stu-id="ce69a-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
