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
ms.openlocfilehash: 0c8398b9e423414f32a391edcd5ea1c709af37f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696553"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="3ccb2-102">CorDebugJITCompilerFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="3ccb2-102">CorDebugJITCompilerFlags Enumeration</span></span>

<span data-ttu-id="3ccb2-103">包含會影響 Managed Just-In-Time (JIT) 編譯器行為的值。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ccb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ccb2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="3ccb2-105">成員</span><span class="sxs-lookup"><span data-stu-id="3ccb2-105">Members</span></span>  
  
|<span data-ttu-id="3ccb2-106">member</span><span class="sxs-lookup"><span data-stu-id="3ccb2-106">Member</span></span>|<span data-ttu-id="3ccb2-107">描述</span><span class="sxs-lookup"><span data-stu-id="3ccb2-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="3ccb2-108">指定編譯器應該追蹤編譯資料，並允許優化。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="3ccb2-109">指定編譯器應該追蹤編譯資料，但停用優化。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="3ccb2-110">指定編譯器應該追蹤編譯資料、停用優化，以及啟用編輯後繼續技術。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ccb2-111">需求</span><span class="sxs-lookup"><span data-stu-id="3ccb2-111">Requirements</span></span>  

 <span data-ttu-id="3ccb2-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ccb2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ccb2-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ccb2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ccb2-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ccb2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ccb2-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ccb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ccb2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ccb2-116">See also</span></span>

- [<span data-ttu-id="3ccb2-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="3ccb2-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
