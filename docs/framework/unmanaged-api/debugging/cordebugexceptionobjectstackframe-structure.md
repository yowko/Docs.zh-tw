---
title: CorDebugExceptionObjectStackFrame 結構
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: 7eccaf984b187e463195bb3804f87bbb2c7ad47b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795920"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="0157a-102">CorDebugExceptionObjectStackFrame 結構</span><span class="sxs-lookup"><span data-stu-id="0157a-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="0157a-103">代表例外狀況物件所產生的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="0157a-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0157a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0157a-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="0157a-105">成員</span><span class="sxs-lookup"><span data-stu-id="0157a-105">Members</span></span>  
  
|<span data-ttu-id="0157a-106">member</span><span class="sxs-lookup"><span data-stu-id="0157a-106">Member</span></span>|<span data-ttu-id="0157a-107">說明</span><span class="sxs-lookup"><span data-stu-id="0157a-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="0157a-108">目前框架的 ICorDebugModule 物件指標。</span><span class="sxs-lookup"><span data-stu-id="0157a-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="0157a-109">目前框架的指令指標（EIP/RIP）的值。</span><span class="sxs-lookup"><span data-stu-id="0157a-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="0157a-110">目前框架的方法 token。</span><span class="sxs-lookup"><span data-stu-id="0157a-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="0157a-111">值，指出框架是否為外部例外狀況中的最後一個框架。</span><span class="sxs-lookup"><span data-stu-id="0157a-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0157a-112">備註</span><span class="sxs-lookup"><span data-stu-id="0157a-112">Remarks</span></span>  
 <span data-ttu-id="0157a-113">呼叫端不再使用時，必須釋放 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="0157a-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0157a-114">需求</span><span class="sxs-lookup"><span data-stu-id="0157a-114">Requirements</span></span>  
 <span data-ttu-id="0157a-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0157a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0157a-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0157a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0157a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0157a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0157a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0157a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0157a-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="0157a-119">See also</span></span>

- [<span data-ttu-id="0157a-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="0157a-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0157a-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="0157a-121">Debugging</span></span>](index.md)
