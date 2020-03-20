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
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179298"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="a336b-102">COR_IL_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="a336b-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="a336b-103">指定函式相關位移中的變更。</span><span class="sxs-lookup"><span data-stu-id="a336b-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a336b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a336b-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="a336b-105">成員</span><span class="sxs-lookup"><span data-stu-id="a336b-105">Members</span></span>  
  
|<span data-ttu-id="a336b-106">member</span><span class="sxs-lookup"><span data-stu-id="a336b-106">Member</span></span>|<span data-ttu-id="a336b-107">描述</span><span class="sxs-lookup"><span data-stu-id="a336b-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="a336b-108">舊的 Microsoft 中間語言 （MSIL） 相對於函數的開頭偏移。</span><span class="sxs-lookup"><span data-stu-id="a336b-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="a336b-109">新的 MSIL 相對於函數的開頭偏移。</span><span class="sxs-lookup"><span data-stu-id="a336b-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="a336b-110">`true`如果已知映射準確;如果映射準確;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="a336b-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a336b-111">備註</span><span class="sxs-lookup"><span data-stu-id="a336b-111">Remarks</span></span>  
 <span data-ttu-id="a336b-112">地圖的格式如下：調試器將假定引用`oldOffset`原始未修改的 MSIL 代碼中的 MSIL 偏移量。</span><span class="sxs-lookup"><span data-stu-id="a336b-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="a336b-113">該`newOffset`參數是指新檢測代碼中的相應 MSIL 偏移量。</span><span class="sxs-lookup"><span data-stu-id="a336b-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="a336b-114">為了正常工作，應滿足以下要求：</span><span class="sxs-lookup"><span data-stu-id="a336b-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="a336b-115">地圖應按昇冪排序。</span><span class="sxs-lookup"><span data-stu-id="a336b-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="a336b-116">不應重新排序已檢測的 MSIL 代碼。</span><span class="sxs-lookup"><span data-stu-id="a336b-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="a336b-117">不應刪除原始 MSIL 代碼。</span><span class="sxs-lookup"><span data-stu-id="a336b-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="a336b-118">地圖應包括用於對應程式資料庫 （PDB） 檔中的所有序列點的條目。</span><span class="sxs-lookup"><span data-stu-id="a336b-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="a336b-119">地圖不會插值缺少的條目。</span><span class="sxs-lookup"><span data-stu-id="a336b-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="a336b-120">下面的示例顯示地圖及其結果。</span><span class="sxs-lookup"><span data-stu-id="a336b-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="a336b-121">地圖：</span><span class="sxs-lookup"><span data-stu-id="a336b-121">Map:</span></span>  
  
- <span data-ttu-id="a336b-122">0 舊偏移，0 新偏移</span><span class="sxs-lookup"><span data-stu-id="a336b-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="a336b-123">5 個舊偏移，10 個新偏移</span><span class="sxs-lookup"><span data-stu-id="a336b-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="a336b-124">9 個舊偏移，20 個新偏移</span><span class="sxs-lookup"><span data-stu-id="a336b-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="a336b-125">結果：</span><span class="sxs-lookup"><span data-stu-id="a336b-125">Results:</span></span>  
  
- <span data-ttu-id="a336b-126">舊偏移 0、1、2、3 或 4 將映射到新的偏移量 0。</span><span class="sxs-lookup"><span data-stu-id="a336b-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="a336b-127">舊偏移 5、6、7 或 8 將映射到新的偏移量 10。</span><span class="sxs-lookup"><span data-stu-id="a336b-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="a336b-128">舊偏移量為 9 或更高，將映射到新的偏移量 20。</span><span class="sxs-lookup"><span data-stu-id="a336b-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="a336b-129">新的偏移量為 0、1、2、3、4、5、6、7、8 或 9 將映射到舊偏移 0。</span><span class="sxs-lookup"><span data-stu-id="a336b-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="a336b-130">10、11、12、13、14、15、16、17、18 或 19 的新偏移將映射到舊偏移 5。</span><span class="sxs-lookup"><span data-stu-id="a336b-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="a336b-131">新的偏移量為 20 或更高，將映射到舊偏移 9。</span><span class="sxs-lookup"><span data-stu-id="a336b-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a336b-132">需求</span><span class="sxs-lookup"><span data-stu-id="a336b-132">Requirements</span></span>  
 <span data-ttu-id="a336b-133">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a336b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a336b-134">**標題：** 科爾科調試.idl， 科爾普羅芬.伊德爾</span><span class="sxs-lookup"><span data-stu-id="a336b-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="a336b-135">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a336b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a336b-136">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a336b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a336b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a336b-137">See also</span></span>

- [<span data-ttu-id="a336b-138">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="a336b-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a336b-139">偵錯</span><span class="sxs-lookup"><span data-stu-id="a336b-139">Debugging</span></span>](index.md)
