---
title: CorDebugJITCompilerFlags 列舉
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66a8ba59d221bb3fa2e815a1cbcfa79c474666cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792726"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="0bf45-102">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="0bf45-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="0bf45-103">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="0bf45-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf45-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bf45-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0bf45-105">成員</span><span class="sxs-lookup"><span data-stu-id="0bf45-105">Members</span></span>  
  
|<span data-ttu-id="0bf45-106">成員</span><span class="sxs-lookup"><span data-stu-id="0bf45-106">Member</span></span>|<span data-ttu-id="0bf45-107">描述</span><span class="sxs-lookup"><span data-stu-id="0bf45-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="0bf45-108">指定編譯器應追蹤編譯資料，並可讓最佳化。</span><span class="sxs-lookup"><span data-stu-id="0bf45-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="0bf45-109">指定編譯器應追蹤編譯資料，但是會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="0bf45-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="0bf45-110">指定編譯器應追蹤編譯資料，會停用最佳化，以及啟用編輯後繼續的技術。</span><span class="sxs-lookup"><span data-stu-id="0bf45-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bf45-111">需求</span><span class="sxs-lookup"><span data-stu-id="0bf45-111">Requirements</span></span>  
 <span data-ttu-id="0bf45-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf45-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bf45-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bf45-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bf45-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bf45-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bf45-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bf45-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf45-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bf45-116">See also</span></span>

- [<span data-ttu-id="0bf45-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="0bf45-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
