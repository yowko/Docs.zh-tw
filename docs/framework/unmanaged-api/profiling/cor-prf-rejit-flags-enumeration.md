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
ms.openlocfilehash: c616cb45eadab3a55aa76526d530cb2841e6d5fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974108"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="82bba-102">COR_PRF_REJIT_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="82bba-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="82bba-103">包含值, 指出[ICorProfilerInfo10:: RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md) API 的行為。</span><span class="sxs-lookup"><span data-stu-id="82bba-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82bba-104">語法</span><span class="sxs-lookup"><span data-stu-id="82bba-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="82bba-105">成員</span><span class="sxs-lookup"><span data-stu-id="82bba-105">Members</span></span>  
  
|<span data-ttu-id="82bba-106">成員</span><span class="sxs-lookup"><span data-stu-id="82bba-106">Member</span></span>|<span data-ttu-id="82bba-107">說明</span><span class="sxs-lookup"><span data-stu-id="82bba-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="82bba-108">ReJITted 方法將會被封鎖, 而無法在其他方法中內嵌。</span><span class="sxs-lookup"><span data-stu-id="82bba-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="82bba-109">針對`GetFunctionParameters`內嵌要求要 ReJITted 之方法的任何方法, 接收回呼。</span><span class="sxs-lookup"><span data-stu-id="82bba-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="82bba-110">需求</span><span class="sxs-lookup"><span data-stu-id="82bba-110">Requirements</span></span>  
 <span data-ttu-id="82bba-111">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="82bba-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="82bba-112">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="82bba-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82bba-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82bba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82bba-114">**.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82bba-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="82bba-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82bba-115">See also</span></span>

- [<span data-ttu-id="82bba-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="82bba-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
