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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177104"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="6f503-102">COR_PRF_REJIT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="6f503-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="6f503-103">包含指示[ICorProfilerInfo10：：請求 ReJITWithinliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API 應如何使用的值。</span><span class="sxs-lookup"><span data-stu-id="6f503-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f503-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f503-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6f503-105">成員</span><span class="sxs-lookup"><span data-stu-id="6f503-105">Members</span></span>  
  
|<span data-ttu-id="6f503-106">member</span><span class="sxs-lookup"><span data-stu-id="6f503-106">Member</span></span>|<span data-ttu-id="6f503-107">描述</span><span class="sxs-lookup"><span data-stu-id="6f503-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="6f503-108">重新 JITed 方法將阻止在其他方法中內聯。</span><span class="sxs-lookup"><span data-stu-id="6f503-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="6f503-109">接收`GetFunctionParameters`任何內聯請求重新JITted的方法的方法的回檔。</span><span class="sxs-lookup"><span data-stu-id="6f503-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="6f503-110">需求</span><span class="sxs-lookup"><span data-stu-id="6f503-110">Requirements</span></span>  
 <span data-ttu-id="6f503-111">**平臺：** 請參閱[.NET Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="6f503-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="6f503-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f503-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f503-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f503-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f503-114">**.NET 框架版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f503-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6f503-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f503-115">See also</span></span>

- [<span data-ttu-id="6f503-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="6f503-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
