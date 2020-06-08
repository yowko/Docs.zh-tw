---
title: COR_PRF_FUNCTION 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 856e01c7934709a17556aa53851204bf6a917de8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500932"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="6d87f-102">COR_PRF_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="6d87f-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="6d87f-103">將其 ID 與其重新編譯版本的 ID 合併在一起，以提供函式的唯一表示法。</span><span class="sxs-lookup"><span data-stu-id="6d87f-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d87f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d87f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="6d87f-105">成員</span><span class="sxs-lookup"><span data-stu-id="6d87f-105">Members</span></span>  
  
|<span data-ttu-id="6d87f-106">成員</span><span class="sxs-lookup"><span data-stu-id="6d87f-106">Member</span></span>|<span data-ttu-id="6d87f-107">說明</span><span class="sxs-lookup"><span data-stu-id="6d87f-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="6d87f-108">函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6d87f-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="6d87f-109">重新編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6d87f-109">The ID of the recompiled function.</span></span> <span data-ttu-id="6d87f-110">值為0（零）代表函式的原始版本。</span><span class="sxs-lookup"><span data-stu-id="6d87f-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d87f-111">備註</span><span class="sxs-lookup"><span data-stu-id="6d87f-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d87f-112">需求</span><span class="sxs-lookup"><span data-stu-id="6d87f-112">Requirements</span></span>  
 <span data-ttu-id="6d87f-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d87f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d87f-114">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="6d87f-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6d87f-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d87f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d87f-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d87f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d87f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d87f-117">See also</span></span>

- [<span data-ttu-id="6d87f-118">分析結構</span><span class="sxs-lookup"><span data-stu-id="6d87f-118">Profiling Structures</span></span>](profiling-structures.md)
