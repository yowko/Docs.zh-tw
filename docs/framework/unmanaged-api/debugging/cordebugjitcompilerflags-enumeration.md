---
title: "CorDebugJITCompilerFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlags
helpviewer_keywords: CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfb78a160a7a6b9f50174fc8bb177cfd8d3f9383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="aa798-102">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="aa798-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="aa798-103">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="aa798-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa798-104">語法</span><span class="sxs-lookup"><span data-stu-id="aa798-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="aa798-105">成員</span><span class="sxs-lookup"><span data-stu-id="aa798-105">Members</span></span>  
  
|<span data-ttu-id="aa798-106">成員</span><span class="sxs-lookup"><span data-stu-id="aa798-106">Member</span></span>|<span data-ttu-id="aa798-107">描述</span><span class="sxs-lookup"><span data-stu-id="aa798-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="aa798-108">指定編譯器應該追蹤編譯資料，並允許最佳化。</span><span class="sxs-lookup"><span data-stu-id="aa798-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="aa798-109">指定編譯器應追蹤編譯資料，但停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="aa798-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="aa798-110">指定編譯器應該追蹤編譯資料，停用最佳化，並啟用編輯後繼續的技術。</span><span class="sxs-lookup"><span data-stu-id="aa798-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa798-111">需求</span><span class="sxs-lookup"><span data-stu-id="aa798-111">Requirements</span></span>  
 <span data-ttu-id="aa798-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa798-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa798-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa798-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa798-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa798-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa798-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa798-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa798-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa798-116">See Also</span></span>  
 [<span data-ttu-id="aa798-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="aa798-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
