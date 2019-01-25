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
ms.openlocfilehash: 4ef262fcae117b27f06d4dba3b2087028b5cfa65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743253"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="2129f-102">CorDebugJITCompilerFlagsDeprecated 列舉</span><span class="sxs-lookup"><span data-stu-id="2129f-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="2129f-103">這個列舉型別已經過時。</span><span class="sxs-lookup"><span data-stu-id="2129f-103">This enumeration is obsolete.</span></span> <span data-ttu-id="2129f-104">使用`CORDEBUG_JIT_DEFAULT`隸屬[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉改。</span><span class="sxs-lookup"><span data-stu-id="2129f-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2129f-105">語法</span><span class="sxs-lookup"><span data-stu-id="2129f-105">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="2129f-106">成員</span><span class="sxs-lookup"><span data-stu-id="2129f-106">Members</span></span>  
  
|<span data-ttu-id="2129f-107">成員</span><span class="sxs-lookup"><span data-stu-id="2129f-107">Member</span></span>|<span data-ttu-id="2129f-108">描述</span><span class="sxs-lookup"><span data-stu-id="2129f-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="2129f-109">請改用 `CORDEBUG_JIT_DEFAULT`。</span><span class="sxs-lookup"><span data-stu-id="2129f-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2129f-110">需求</span><span class="sxs-lookup"><span data-stu-id="2129f-110">Requirements</span></span>  
 <span data-ttu-id="2129f-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2129f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2129f-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2129f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2129f-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2129f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2129f-114">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="2129f-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2129f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2129f-115">See also</span></span>
- [<span data-ttu-id="2129f-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="2129f-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
