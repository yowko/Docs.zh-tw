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
ms.openlocfilehash: 8be8ce36b557831bc0997dd1c69abb924390d051
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795816"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="4e0f6-102">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="4e0f6-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="4e0f6-103">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="4e0f6-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e0f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e0f6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4e0f6-105">成員</span><span class="sxs-lookup"><span data-stu-id="4e0f6-105">Members</span></span>  
  
|<span data-ttu-id="4e0f6-106">member</span><span class="sxs-lookup"><span data-stu-id="4e0f6-106">Member</span></span>|<span data-ttu-id="4e0f6-107">說明</span><span class="sxs-lookup"><span data-stu-id="4e0f6-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="4e0f6-108">指定編譯器應該追蹤編譯資料，並允許優化。</span><span class="sxs-lookup"><span data-stu-id="4e0f6-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="4e0f6-109">指定編譯器應該追蹤編譯資料，但停用優化。</span><span class="sxs-lookup"><span data-stu-id="4e0f6-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="4e0f6-110">指定編譯器應該追蹤編譯資料、停用優化，並啟用編輯後繼續技術。</span><span class="sxs-lookup"><span data-stu-id="4e0f6-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e0f6-111">需求</span><span class="sxs-lookup"><span data-stu-id="4e0f6-111">Requirements</span></span>  
 <span data-ttu-id="4e0f6-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e0f6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e0f6-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e0f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e0f6-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e0f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e0f6-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e0f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e0f6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e0f6-116">See also</span></span>

- [<span data-ttu-id="4e0f6-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="4e0f6-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
