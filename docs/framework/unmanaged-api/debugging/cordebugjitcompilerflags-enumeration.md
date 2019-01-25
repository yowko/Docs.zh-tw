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
ms.openlocfilehash: 512122d264e0817b89e8a371f57f11d31f7c4380
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639626"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="bb87b-102">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="bb87b-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="bb87b-103">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="bb87b-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb87b-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb87b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bb87b-105">成員</span><span class="sxs-lookup"><span data-stu-id="bb87b-105">Members</span></span>  
  
|<span data-ttu-id="bb87b-106">成員</span><span class="sxs-lookup"><span data-stu-id="bb87b-106">Member</span></span>|<span data-ttu-id="bb87b-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb87b-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="bb87b-108">指定編譯器應追蹤編譯資料，並可讓最佳化。</span><span class="sxs-lookup"><span data-stu-id="bb87b-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="bb87b-109">指定編譯器應追蹤編譯資料，但是會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="bb87b-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="bb87b-110">指定編譯器應追蹤編譯資料，會停用最佳化，以及啟用編輯後繼續的技術。</span><span class="sxs-lookup"><span data-stu-id="bb87b-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb87b-111">需求</span><span class="sxs-lookup"><span data-stu-id="bb87b-111">Requirements</span></span>  
 <span data-ttu-id="bb87b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb87b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb87b-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb87b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb87b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb87b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb87b-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb87b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb87b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb87b-116">See also</span></span>
- [<span data-ttu-id="bb87b-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="bb87b-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
