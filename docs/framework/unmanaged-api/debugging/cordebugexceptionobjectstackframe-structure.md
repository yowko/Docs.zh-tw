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
ms.openlocfilehash: 9b904596ed1cce4c4cf2676676508dfb3851e8ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712673"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="8e932-102">CorDebugExceptionObjectStackFrame 結構</span><span class="sxs-lookup"><span data-stu-id="8e932-102">CorDebugExceptionObjectStackFrame Structure</span></span>

<span data-ttu-id="8e932-103">代表例外狀況物件所產生的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="8e932-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e932-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e932-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="8e932-105">成員</span><span class="sxs-lookup"><span data-stu-id="8e932-105">Members</span></span>  
  
|<span data-ttu-id="8e932-106">member</span><span class="sxs-lookup"><span data-stu-id="8e932-106">Member</span></span>|<span data-ttu-id="8e932-107">描述</span><span class="sxs-lookup"><span data-stu-id="8e932-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="8e932-108">目前框架的 ICorDebugModule 物件指標。</span><span class="sxs-lookup"><span data-stu-id="8e932-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="8e932-109">指令指標的值 (目前框架的 EIP/RIP) 。</span><span class="sxs-lookup"><span data-stu-id="8e932-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="8e932-110">目前框架的方法標記。</span><span class="sxs-lookup"><span data-stu-id="8e932-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="8e932-111">值，指出框架是否為外部例外狀況中的最後一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="8e932-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e932-112">備註</span><span class="sxs-lookup"><span data-stu-id="8e932-112">Remarks</span></span>  

 <span data-ttu-id="8e932-113">當呼叫端不再使用時，呼叫端必須釋放 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="8e932-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e932-114">需求</span><span class="sxs-lookup"><span data-stu-id="8e932-114">Requirements</span></span>  

 <span data-ttu-id="8e932-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e932-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e932-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e932-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e932-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e932-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e932-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e932-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e932-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e932-119">See also</span></span>

- [<span data-ttu-id="8e932-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="8e932-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="8e932-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="8e932-121">Debugging</span></span>](index.md)
