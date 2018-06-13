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
ms.openlocfilehash: acf2ba752ace49ae288857dc22819a8e7e429a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424049"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="73645-102">StackTrace_SimpleContext 結構</span><span class="sxs-lookup"><span data-stu-id="73645-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="73645-103">提供可用來代替完整 `CONTEXT` 結構的簡單內容。</span><span class="sxs-lookup"><span data-stu-id="73645-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73645-104">語法</span><span class="sxs-lookup"><span data-stu-id="73645-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="73645-105">成員</span><span class="sxs-lookup"><span data-stu-id="73645-105">Members</span></span>  
  
|<span data-ttu-id="73645-106">成員</span><span class="sxs-lookup"><span data-stu-id="73645-106">Member</span></span>|<span data-ttu-id="73645-107">描述</span><span class="sxs-lookup"><span data-stu-id="73645-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="73645-108">堆疊指標或在 x86 上的 enter 堆疊指標 (ESP) 平台。</span><span class="sxs-lookup"><span data-stu-id="73645-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="73645-109">框架位移或 ebp 暫存器，在 x86 平台。</span><span class="sxs-lookup"><span data-stu-id="73645-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="73645-110">指令指標使用或在 x86 上的 enter 指令指標 (EIP) 平台。</span><span class="sxs-lookup"><span data-stu-id="73645-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73645-111">備註</span><span class="sxs-lookup"><span data-stu-id="73645-111">Remarks</span></span>  
 <span data-ttu-id="73645-112">因為堆疊追蹤函式通常需要只傳回位址、 框架位移，並堆疊位址，您可以選擇性地使用`SimpleContext`結構，而不是大型`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="73645-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73645-113">需求</span><span class="sxs-lookup"><span data-stu-id="73645-113">Requirements</span></span>  
 <span data-ttu-id="73645-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73645-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73645-115">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="73645-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="73645-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73645-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73645-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73645-117">See Also</span></span>  
 [<span data-ttu-id="73645-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="73645-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="73645-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="73645-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
