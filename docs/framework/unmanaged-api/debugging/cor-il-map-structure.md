---
title: COR_IL_MAP 結構
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6d8023c7ac6d917c9df40fb18316ddc12df5ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609411"
---
# <a name="corilmap-structure"></a><span data-ttu-id="b43d3-102">COR_IL_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="b43d3-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="b43d3-103">指定函式相關位移中的變更。</span><span class="sxs-lookup"><span data-stu-id="b43d3-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b43d3-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="b43d3-105">成員</span><span class="sxs-lookup"><span data-stu-id="b43d3-105">Members</span></span>  
  
|<span data-ttu-id="b43d3-106">成員</span><span class="sxs-lookup"><span data-stu-id="b43d3-106">Member</span></span>|<span data-ttu-id="b43d3-107">描述</span><span class="sxs-lookup"><span data-stu-id="b43d3-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="b43d3-108">舊 Microsoft intermediate language (MSIL) 位移相對於函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="b43d3-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="b43d3-109">新的 MSIL 位移相對於函式的開頭。</span><span class="sxs-lookup"><span data-stu-id="b43d3-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="b43d3-110">`true` 如果對應已知為正確;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="b43d3-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b43d3-111">備註</span><span class="sxs-lookup"><span data-stu-id="b43d3-111">Remarks</span></span>  
 <span data-ttu-id="b43d3-112">對應的格式如下所示：偵錯工具會假設`oldOffset`指原始、 未修改 MSIL 程式碼中的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="b43d3-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="b43d3-113">`newOffset`參數會參考新的已檢測的程式碼中對應的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="b43d3-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="b43d3-114">逐步執行才能正常運作，應該符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="b43d3-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="b43d3-115">此對應應該以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="b43d3-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="b43d3-116">已檢測的 MSIL 程式碼應該不會重新排列。</span><span class="sxs-lookup"><span data-stu-id="b43d3-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="b43d3-117">原始的 MSIL 程式碼應該不會移除。</span><span class="sxs-lookup"><span data-stu-id="b43d3-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="b43d3-118">對應應該包含對應用程式資料庫 (PDB) 檔案中的所有序列點的項目。</span><span class="sxs-lookup"><span data-stu-id="b43d3-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="b43d3-119">對應不會插補遺漏的項目。</span><span class="sxs-lookup"><span data-stu-id="b43d3-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="b43d3-120">下列範例會顯示對應和它的結果。</span><span class="sxs-lookup"><span data-stu-id="b43d3-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="b43d3-121">對應：</span><span class="sxs-lookup"><span data-stu-id="b43d3-121">Map:</span></span>  
  
- <span data-ttu-id="b43d3-122">0 的舊位移、 0 的新位移</span><span class="sxs-lookup"><span data-stu-id="b43d3-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="b43d3-123">5 的舊位移、 10 個新的位移</span><span class="sxs-lookup"><span data-stu-id="b43d3-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="b43d3-124">9 的舊位移、 20 的新位移</span><span class="sxs-lookup"><span data-stu-id="b43d3-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="b43d3-125">結果：</span><span class="sxs-lookup"><span data-stu-id="b43d3-125">Results:</span></span>  
  
- <span data-ttu-id="b43d3-126">0、 1、 2、 3 或 4 的舊位移會對應至新的位移為 0。</span><span class="sxs-lookup"><span data-stu-id="b43d3-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="b43d3-127">5、 6、 7 或 8 的舊位移會對應至 10 的新位移。</span><span class="sxs-lookup"><span data-stu-id="b43d3-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="b43d3-128">9 或更新版本的舊位移會對應至新的位移 20。</span><span class="sxs-lookup"><span data-stu-id="b43d3-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="b43d3-129">0、 1、 2、 3、 4、 5、 6、 7、 8 或 9 新位移會對應至舊的位移 0。</span><span class="sxs-lookup"><span data-stu-id="b43d3-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="b43d3-130">新的位移，10、 11、 12、 13、 14、 15、 16、 17、 18 或 19 的會對應至舊位移 5。</span><span class="sxs-lookup"><span data-stu-id="b43d3-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="b43d3-131">20 或更高版本的新位移會對應至舊位移 9。</span><span class="sxs-lookup"><span data-stu-id="b43d3-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43d3-132">需求</span><span class="sxs-lookup"><span data-stu-id="b43d3-132">Requirements</span></span>  
 <span data-ttu-id="b43d3-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b43d3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43d3-134">**標頭：** CorDebug.idl、 CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b43d3-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="b43d3-135">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b43d3-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43d3-136">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43d3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43d3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b43d3-137">See also</span></span>

- [<span data-ttu-id="b43d3-138">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="b43d3-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b43d3-139">偵錯</span><span class="sxs-lookup"><span data-stu-id="b43d3-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
