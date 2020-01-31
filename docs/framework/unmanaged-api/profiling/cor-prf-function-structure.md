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
ms.openlocfilehash: 14dcb251e25b5bd502c8d514a6dc35778fbe9f73
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867226"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="65d06-102">COR_PRF_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="65d06-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="65d06-103">將其 ID 與其重新編譯版本的 ID 合併在一起，以提供函式的唯一表示法。</span><span class="sxs-lookup"><span data-stu-id="65d06-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d06-104">語法</span><span class="sxs-lookup"><span data-stu-id="65d06-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="65d06-105">Members</span><span class="sxs-lookup"><span data-stu-id="65d06-105">Members</span></span>  
  
|<span data-ttu-id="65d06-106">成員</span><span class="sxs-lookup"><span data-stu-id="65d06-106">Member</span></span>|<span data-ttu-id="65d06-107">描述</span><span class="sxs-lookup"><span data-stu-id="65d06-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="65d06-108">函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="65d06-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="65d06-109">重新編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="65d06-109">The ID of the recompiled function.</span></span> <span data-ttu-id="65d06-110">值為0（零）代表函式的原始版本。</span><span class="sxs-lookup"><span data-stu-id="65d06-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65d06-111">備註</span><span class="sxs-lookup"><span data-stu-id="65d06-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d06-112">需求</span><span class="sxs-lookup"><span data-stu-id="65d06-112">Requirements</span></span>  
 <span data-ttu-id="65d06-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65d06-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d06-114">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="65d06-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="65d06-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65d06-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65d06-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d06-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d06-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="65d06-117">See also</span></span>

- [<span data-ttu-id="65d06-118">分析結構</span><span class="sxs-lookup"><span data-stu-id="65d06-118">Profiling Structures</span></span>](profiling-structures.md)
