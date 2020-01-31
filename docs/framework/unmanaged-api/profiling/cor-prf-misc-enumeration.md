---
title: COR_PRF_MISC 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: fe27c0fca6d38b4cff6cac2b9778cf2be68903a3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867122"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="ee703-102">COR_PRF_MISC 列舉</span><span class="sxs-lookup"><span data-stu-id="ee703-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="ee703-103">包含指定特定識別項的常數值。</span><span class="sxs-lookup"><span data-stu-id="ee703-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee703-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee703-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="ee703-105">Members</span><span class="sxs-lookup"><span data-stu-id="ee703-105">Members</span></span>  
  
|<span data-ttu-id="ee703-106">成員</span><span class="sxs-lookup"><span data-stu-id="ee703-106">Member</span></span>|<span data-ttu-id="ee703-107">描述</span><span class="sxs-lookup"><span data-stu-id="ee703-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="ee703-108">尚未附加至元件之模組的[ICorProfilerInfo：： GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md)所使用的預設識別碼。</span><span class="sxs-lookup"><span data-stu-id="ee703-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="ee703-109">不屬於類別之全域常數的預設類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="ee703-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="ee703-110">不屬於模組之全域物件的預設模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="ee703-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee703-111">需求</span><span class="sxs-lookup"><span data-stu-id="ee703-111">Requirements</span></span>  
 <span data-ttu-id="ee703-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee703-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee703-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee703-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee703-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee703-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee703-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee703-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee703-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee703-116">See also</span></span>

- [<span data-ttu-id="ee703-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="ee703-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
