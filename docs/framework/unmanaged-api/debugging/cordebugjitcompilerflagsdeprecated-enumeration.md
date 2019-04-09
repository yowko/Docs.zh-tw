---
title: CorDebugJITCompilerFlagsDeprecated 列舉
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f15a4557be0dc633fb9ecda5916896e340f00da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136886"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="1c1f7-102">CorDebugJITCompilerFlagsDeprecated 列舉</span><span class="sxs-lookup"><span data-stu-id="1c1f7-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="1c1f7-103">這個列舉型別已經過時。</span><span class="sxs-lookup"><span data-stu-id="1c1f7-103">This enumeration is obsolete.</span></span> <span data-ttu-id="1c1f7-104">使用`CORDEBUG_JIT_DEFAULT`隸屬[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉改。</span><span class="sxs-lookup"><span data-stu-id="1c1f7-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1f7-105">語法</span><span class="sxs-lookup"><span data-stu-id="1c1f7-105">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="1c1f7-106">成員</span><span class="sxs-lookup"><span data-stu-id="1c1f7-106">Members</span></span>  
  
|<span data-ttu-id="1c1f7-107">成員</span><span class="sxs-lookup"><span data-stu-id="1c1f7-107">Member</span></span>|<span data-ttu-id="1c1f7-108">描述</span><span class="sxs-lookup"><span data-stu-id="1c1f7-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="1c1f7-109">請改用 `CORDEBUG_JIT_DEFAULT`。</span><span class="sxs-lookup"><span data-stu-id="1c1f7-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c1f7-110">需求</span><span class="sxs-lookup"><span data-stu-id="1c1f7-110">Requirements</span></span>  
 <span data-ttu-id="1c1f7-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c1f7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c1f7-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c1f7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c1f7-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c1f7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c1f7-114">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1c1f7-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1f7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c1f7-115">See also</span></span>

- [<span data-ttu-id="1c1f7-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="1c1f7-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
