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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4cd4d353c22921ed3dba1dc08fe2cee7e429f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996316"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="e71ad-102">CorDebugExceptionObjectStackFrame 結構</span><span class="sxs-lookup"><span data-stu-id="e71ad-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="e71ad-103">代表例外狀況物件所產生的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="e71ad-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="e71ad-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="e71ad-105">成員</span><span class="sxs-lookup"><span data-stu-id="e71ad-105">Members</span></span>  
  
|<span data-ttu-id="e71ad-106">成員</span><span class="sxs-lookup"><span data-stu-id="e71ad-106">Member</span></span>|<span data-ttu-id="e71ad-107">描述</span><span class="sxs-lookup"><span data-stu-id="e71ad-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="e71ad-108">ICorDebugModule 物件目前畫面格指標。</span><span class="sxs-lookup"><span data-stu-id="e71ad-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="e71ad-109">指令指標 (EIP/RIP) 目前畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="e71ad-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="e71ad-110">目前的框架方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e71ad-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="e71ad-111">值，指出框架是否為外部例外狀況的最後一個框架。</span><span class="sxs-lookup"><span data-stu-id="e71ad-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e71ad-112">備註</span><span class="sxs-lookup"><span data-stu-id="e71ad-112">Remarks</span></span>  
 <span data-ttu-id="e71ad-113">呼叫端必須釋放 ICorDebugModule 物件的指標之後就無法再使用中。</span><span class="sxs-lookup"><span data-stu-id="e71ad-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e71ad-114">需求</span><span class="sxs-lookup"><span data-stu-id="e71ad-114">Requirements</span></span>  
 <span data-ttu-id="e71ad-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e71ad-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e71ad-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e71ad-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e71ad-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e71ad-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e71ad-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e71ad-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71ad-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e71ad-119">See also</span></span>

- [<span data-ttu-id="e71ad-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="e71ad-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="e71ad-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="e71ad-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
