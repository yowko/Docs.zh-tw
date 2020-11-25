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
ms.openlocfilehash: fb6b5d43e60b52c867535c42d59a098ef3c959bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726379"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="5e475-102">COR_IL_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="5e475-102">COR_IL_MAP Structure</span></span>

<span data-ttu-id="5e475-103">指定函式相關位移中的變更。</span><span class="sxs-lookup"><span data-stu-id="5e475-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e475-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e475-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="5e475-105">成員</span><span class="sxs-lookup"><span data-stu-id="5e475-105">Members</span></span>  
  
|<span data-ttu-id="5e475-106">member</span><span class="sxs-lookup"><span data-stu-id="5e475-106">Member</span></span>|<span data-ttu-id="5e475-107">描述</span><span class="sxs-lookup"><span data-stu-id="5e475-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="5e475-108">舊版 Microsoft 中繼語言 (MSIL) 相對於函數開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="5e475-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="5e475-109">相對於函數開頭的新 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="5e475-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="5e475-110">`true` 如果已知對應是正確的，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="5e475-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e475-111">備註</span><span class="sxs-lookup"><span data-stu-id="5e475-111">Remarks</span></span>  

 <span data-ttu-id="5e475-112">對應的格式如下所示：偵錯工具會假設 `oldOffset` 參考原始、未修改之 msil 程式碼內的 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="5e475-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="5e475-113">`newOffset`參數會參考新檢測程式碼內的對應 MSIL 位移。</span><span class="sxs-lookup"><span data-stu-id="5e475-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="5e475-114">若要讓逐步執行正常運作，應符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="5e475-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="5e475-115">地圖應該以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="5e475-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="5e475-116">已檢測的 MSIL 程式碼不應重新排序。</span><span class="sxs-lookup"><span data-stu-id="5e475-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="5e475-117">不應移除原始 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e475-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="5e475-118">對應應包含專案，以對應程式資料庫 (PDB) 檔中的所有序列點。</span><span class="sxs-lookup"><span data-stu-id="5e475-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="5e475-119">地圖不會插補遺漏的專案。</span><span class="sxs-lookup"><span data-stu-id="5e475-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="5e475-120">下列範例顯示對應和其結果。</span><span class="sxs-lookup"><span data-stu-id="5e475-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="5e475-121">地圖：</span><span class="sxs-lookup"><span data-stu-id="5e475-121">Map:</span></span>  
  
- <span data-ttu-id="5e475-122">0舊位移，0新位移</span><span class="sxs-lookup"><span data-stu-id="5e475-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="5e475-123">5個舊的位移，10個新的位移</span><span class="sxs-lookup"><span data-stu-id="5e475-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="5e475-124">9個舊的位移，20個新的位移</span><span class="sxs-lookup"><span data-stu-id="5e475-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="5e475-125">結果：</span><span class="sxs-lookup"><span data-stu-id="5e475-125">Results:</span></span>  
  
- <span data-ttu-id="5e475-126">舊的位移0、1、2、3或4將會對應至新的位移0。</span><span class="sxs-lookup"><span data-stu-id="5e475-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="5e475-127">舊的位移5、6、7或8將會對應至新的位移10。</span><span class="sxs-lookup"><span data-stu-id="5e475-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="5e475-128">舊位移9或更高版本將會對應至新的位移20。</span><span class="sxs-lookup"><span data-stu-id="5e475-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="5e475-129">新的位移0、1、2、3、4、5、6、7、8或9將會對應到舊的位移0。</span><span class="sxs-lookup"><span data-stu-id="5e475-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="5e475-130">新的位移10、11、12、13、14、15、16、17、18或19將會對應到舊的位移5。</span><span class="sxs-lookup"><span data-stu-id="5e475-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="5e475-131">新的位移20或更高的位移會對應到舊的位移9。</span><span class="sxs-lookup"><span data-stu-id="5e475-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e475-132">需求</span><span class="sxs-lookup"><span data-stu-id="5e475-132">Requirements</span></span>  

 <span data-ttu-id="5e475-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e475-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e475-134">**標頭：** Cordebug.h .idl，Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="5e475-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="5e475-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e475-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e475-136">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e475-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e475-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e475-137">See also</span></span>

- [<span data-ttu-id="5e475-138">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="5e475-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5e475-139">偵錯</span><span class="sxs-lookup"><span data-stu-id="5e475-139">Debugging</span></span>](index.md)
