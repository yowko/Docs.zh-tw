---
title: "CorDebugExceptionObjectStackFrame 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="df387-102">CorDebugExceptionObjectStackFrame 結構</span><span class="sxs-lookup"><span data-stu-id="df387-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="df387-103">代表例外狀況物件所產生的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="df387-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df387-104">語法</span><span class="sxs-lookup"><span data-stu-id="df387-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="df387-105">成員</span><span class="sxs-lookup"><span data-stu-id="df387-105">Members</span></span>  
  
|<span data-ttu-id="df387-106">成員</span><span class="sxs-lookup"><span data-stu-id="df387-106">Member</span></span>|<span data-ttu-id="df387-107">說明</span><span class="sxs-lookup"><span data-stu-id="df387-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="df387-108">ICorDebugModule 物件目前畫面格指標。</span><span class="sxs-lookup"><span data-stu-id="df387-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="df387-109">指令指標 (EIP/RIP) 目前畫面格的值。</span><span class="sxs-lookup"><span data-stu-id="df387-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="df387-110">目前的框架方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="df387-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="df387-111">值，指出的框架是在外部例外狀況中的最後一個框架。</span><span class="sxs-lookup"><span data-stu-id="df387-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df387-112">備註</span><span class="sxs-lookup"><span data-stu-id="df387-112">Remarks</span></span>  
 <span data-ttu-id="df387-113">呼叫端必須釋放 ICorDebugModule 物件的指標之後就無法再使用中。</span><span class="sxs-lookup"><span data-stu-id="df387-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df387-114">需求</span><span class="sxs-lookup"><span data-stu-id="df387-114">Requirements</span></span>  
 <span data-ttu-id="df387-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df387-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df387-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df387-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df387-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df387-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df387-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df387-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df387-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df387-119">See Also</span></span>  
 [<span data-ttu-id="df387-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="df387-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="df387-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="df387-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
