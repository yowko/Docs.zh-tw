---
title: COR_PRF_REJIT_FLAGS 列舉
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: fabbcd497dc2f321da90188cebbac6ed4e147492
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867083"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="e2acb-102">COR_PRF_REJIT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="e2acb-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="e2acb-103">包含值，指出[ICorProfilerInfo10：： RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 的行為。</span><span class="sxs-lookup"><span data-stu-id="e2acb-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2acb-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2acb-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e2acb-105">Members</span><span class="sxs-lookup"><span data-stu-id="e2acb-105">Members</span></span>  
  
|<span data-ttu-id="e2acb-106">成員</span><span class="sxs-lookup"><span data-stu-id="e2acb-106">Member</span></span>|<span data-ttu-id="e2acb-107">描述</span><span class="sxs-lookup"><span data-stu-id="e2acb-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="e2acb-108">ReJITted 方法將會被封鎖，而無法在其他方法中內嵌。</span><span class="sxs-lookup"><span data-stu-id="e2acb-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="e2acb-109">針對內嵌要求 ReJITted 之方法的任何方法，接收 `GetFunctionParameters` 回呼。</span><span class="sxs-lookup"><span data-stu-id="e2acb-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="e2acb-110">需求</span><span class="sxs-lookup"><span data-stu-id="e2acb-110">Requirements</span></span>  
 <span data-ttu-id="e2acb-111">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="e2acb-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
  
 <span data-ttu-id="e2acb-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2acb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2acb-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2acb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2acb-114">**.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2acb-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="e2acb-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2acb-115">See also</span></span>

- [<span data-ttu-id="e2acb-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="e2acb-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
