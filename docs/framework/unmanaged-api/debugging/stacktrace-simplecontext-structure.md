---
title: StackTrace_SimpleContext 結構
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210421"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="315d4-102">StackTrace_SimpleContext 結構</span><span class="sxs-lookup"><span data-stu-id="315d4-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="315d4-103">提供可用來代替完整 `CONTEXT` 結構的簡單內容。</span><span class="sxs-lookup"><span data-stu-id="315d4-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="315d4-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="315d4-105">成員</span><span class="sxs-lookup"><span data-stu-id="315d4-105">Members</span></span>  
  
|<span data-ttu-id="315d4-106">成員</span><span class="sxs-lookup"><span data-stu-id="315d4-106">Member</span></span>|<span data-ttu-id="315d4-107">描述</span><span class="sxs-lookup"><span data-stu-id="315d4-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="315d4-108">堆疊指標或在 x86 上的 enter 堆疊指標 (ESP) 平台。</span><span class="sxs-lookup"><span data-stu-id="315d4-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="315d4-109">畫面格位移或 EBP 暫存器，在 x86 平台。</span><span class="sxs-lookup"><span data-stu-id="315d4-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="315d4-110">指令指標或輸入指令指標 (EIP) 在 x86 平台。</span><span class="sxs-lookup"><span data-stu-id="315d4-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="315d4-111">備註</span><span class="sxs-lookup"><span data-stu-id="315d4-111">Remarks</span></span>  
 <span data-ttu-id="315d4-112">因為堆疊追蹤函式通常需要只傳回地址、 框架位移並堆疊位址，您可以選擇性地使用`SimpleContext`結構，而不是大型`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="315d4-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="315d4-113">需求</span><span class="sxs-lookup"><span data-stu-id="315d4-113">Requirements</span></span>  
 <span data-ttu-id="315d4-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="315d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="315d4-115">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="315d4-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="315d4-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="315d4-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="315d4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="315d4-117">See also</span></span>

- [<span data-ttu-id="315d4-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="315d4-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="315d4-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="315d4-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
