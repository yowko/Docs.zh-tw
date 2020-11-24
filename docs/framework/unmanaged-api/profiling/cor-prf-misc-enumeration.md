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
ms.openlocfilehash: 5a3c820b52ae9376d769ea9956edc0b8553a1f88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682168"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="f3ebc-102">COR_PRF_MISC 列舉</span><span class="sxs-lookup"><span data-stu-id="f3ebc-102">COR_PRF_MISC Enumeration</span></span>

<span data-ttu-id="f3ebc-103">包含指定特定識別項的常數值。</span><span class="sxs-lookup"><span data-stu-id="f3ebc-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ebc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3ebc-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="f3ebc-105">成員</span><span class="sxs-lookup"><span data-stu-id="f3ebc-105">Members</span></span>  
  
|<span data-ttu-id="f3ebc-106">member</span><span class="sxs-lookup"><span data-stu-id="f3ebc-106">Member</span></span>|<span data-ttu-id="f3ebc-107">描述</span><span class="sxs-lookup"><span data-stu-id="f3ebc-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="f3ebc-108">[ICorProfilerInfo：： GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md)針對尚未附加至元件的模組所使用的預設識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3ebc-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="f3ebc-109">不屬於類別之全域常數的預設類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3ebc-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="f3ebc-110">不屬於模組之全域物件的預設模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3ebc-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3ebc-111">需求</span><span class="sxs-lookup"><span data-stu-id="f3ebc-111">Requirements</span></span>  

 <span data-ttu-id="f3ebc-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ebc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ebc-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3ebc-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3ebc-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3ebc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3ebc-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ebc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ebc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3ebc-116">See also</span></span>

- [<span data-ttu-id="f3ebc-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="f3ebc-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
