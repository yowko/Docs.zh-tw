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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11b36fa4636dd55e539c198a260dcf93da02a237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728956"
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="a126f-102">COR_PRF_MISC 列舉</span><span class="sxs-lookup"><span data-stu-id="a126f-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="a126f-103">包含指定特定識別項的常數值。</span><span class="sxs-lookup"><span data-stu-id="a126f-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a126f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a126f-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="a126f-105">成員</span><span class="sxs-lookup"><span data-stu-id="a126f-105">Members</span></span>  
  
|<span data-ttu-id="a126f-106">成員</span><span class="sxs-lookup"><span data-stu-id="a126f-106">Member</span></span>|<span data-ttu-id="a126f-107">描述</span><span class="sxs-lookup"><span data-stu-id="a126f-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="a126f-108">所使用的預設識別碼[icorprofilerinfo:: Getmoduleinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)尚未附加至組件的模組。</span><span class="sxs-lookup"><span data-stu-id="a126f-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="a126f-109">不屬於類別的全域常數預設類別識別項。</span><span class="sxs-lookup"><span data-stu-id="a126f-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="a126f-110">不屬於模組的全域物件預設模組識別項。</span><span class="sxs-lookup"><span data-stu-id="a126f-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a126f-111">需求</span><span class="sxs-lookup"><span data-stu-id="a126f-111">Requirements</span></span>  
 <span data-ttu-id="a126f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a126f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a126f-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a126f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a126f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a126f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a126f-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a126f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a126f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a126f-116">See also</span></span>
- [<span data-ttu-id="a126f-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="a126f-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
