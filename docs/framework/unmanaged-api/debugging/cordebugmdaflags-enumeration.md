---
title: "CorDebugMDAFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMDAFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMDAFlags
helpviewer_keywords: CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: defd2572d6f925cf557539983308b3b3e900eebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="f587f-102">CorDebugMDAFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="f587f-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="f587f-103">指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="f587f-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f587f-104">語法</span><span class="sxs-lookup"><span data-stu-id="f587f-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f587f-105">成員</span><span class="sxs-lookup"><span data-stu-id="f587f-105">Members</span></span>  
  
|<span data-ttu-id="f587f-106">成員</span><span class="sxs-lookup"><span data-stu-id="f587f-106">Member</span></span>|<span data-ttu-id="f587f-107">描述</span><span class="sxs-lookup"><span data-stu-id="f587f-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="f587f-108">因為 MDA 所引發的進度落後 MDA 已引發所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f587f-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f587f-109">備註</span><span class="sxs-lookup"><span data-stu-id="f587f-109">Remarks</span></span>  
 <span data-ttu-id="f587f-110">呼叫堆疊不會再描述原本引發 MDA，當執行緒被視為具有*順延*。</span><span class="sxs-lookup"><span data-stu-id="f587f-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="f587f-111">這是作業的不尋常的情況下，是作業的無效結束時執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f587f-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f587f-112">需求</span><span class="sxs-lookup"><span data-stu-id="f587f-112">Requirements</span></span>  
 <span data-ttu-id="f587f-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f587f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f587f-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f587f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f587f-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f587f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f587f-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f587f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f587f-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f587f-117">See Also</span></span>  
 [<span data-ttu-id="f587f-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="f587f-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
