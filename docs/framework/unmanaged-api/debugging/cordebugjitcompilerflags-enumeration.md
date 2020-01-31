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
ms.openlocfilehash: 65d7e830b82cc1780826517fe8cff1da0a7d6188
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793898"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="fa68a-102">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="fa68a-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="fa68a-103">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="fa68a-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa68a-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa68a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fa68a-105">Members</span><span class="sxs-lookup"><span data-stu-id="fa68a-105">Members</span></span>  
  
|<span data-ttu-id="fa68a-106">成員</span><span class="sxs-lookup"><span data-stu-id="fa68a-106">Member</span></span>|<span data-ttu-id="fa68a-107">描述</span><span class="sxs-lookup"><span data-stu-id="fa68a-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="fa68a-108">指定編譯器應該追蹤編譯資料，並允許優化。</span><span class="sxs-lookup"><span data-stu-id="fa68a-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="fa68a-109">指定編譯器應該追蹤編譯資料，但停用優化。</span><span class="sxs-lookup"><span data-stu-id="fa68a-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="fa68a-110">指定編譯器應該追蹤編譯資料、停用優化，並啟用編輯後繼續技術。</span><span class="sxs-lookup"><span data-stu-id="fa68a-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa68a-111">需求</span><span class="sxs-lookup"><span data-stu-id="fa68a-111">Requirements</span></span>  
 <span data-ttu-id="fa68a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa68a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa68a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa68a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa68a-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa68a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa68a-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa68a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa68a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa68a-116">See also</span></span>

- [<span data-ttu-id="fa68a-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="fa68a-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
