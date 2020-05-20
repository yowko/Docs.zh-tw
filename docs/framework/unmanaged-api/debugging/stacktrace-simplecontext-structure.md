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
ms.openlocfilehash: 45ae947cda5b4ddadfb10f5b2bdc78a95f031703
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420680"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="348f0-102">StackTrace_SimpleContext 結構</span><span class="sxs-lookup"><span data-stu-id="348f0-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="348f0-103">提供可用來代替完整 `CONTEXT` 結構的簡單內容。</span><span class="sxs-lookup"><span data-stu-id="348f0-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="348f0-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="348f0-105">成員</span><span class="sxs-lookup"><span data-stu-id="348f0-105">Members</span></span>  
  
|<span data-ttu-id="348f0-106">成員</span><span class="sxs-lookup"><span data-stu-id="348f0-106">Member</span></span>|<span data-ttu-id="348f0-107">說明</span><span class="sxs-lookup"><span data-stu-id="348f0-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="348f0-108">堆疊指標，或 x86 平臺上的輸入堆疊指標（ESP）。</span><span class="sxs-lookup"><span data-stu-id="348f0-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="348f0-109">框架位移，或 x86 平臺上的 EBP 暫存器。</span><span class="sxs-lookup"><span data-stu-id="348f0-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="348f0-110">指令指標，或 x86 平臺上的 enter 指令指標（EIP）。</span><span class="sxs-lookup"><span data-stu-id="348f0-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="348f0-111">備註</span><span class="sxs-lookup"><span data-stu-id="348f0-111">Remarks</span></span>  
 <span data-ttu-id="348f0-112">因為堆疊追蹤函數通常只需要傳回位址、框架位移和堆疊位址，所以您可以選擇性地使用結構， `SimpleContext` 而不是大型 `CONTEXT` 結構。</span><span class="sxs-lookup"><span data-stu-id="348f0-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="348f0-113">需求</span><span class="sxs-lookup"><span data-stu-id="348f0-113">Requirements</span></span>  
 <span data-ttu-id="348f0-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="348f0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="348f0-115">**標頭：** SOS_Stacktrace。h</span><span class="sxs-lookup"><span data-stu-id="348f0-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="348f0-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="348f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348f0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="348f0-117">See also</span></span>

- [<span data-ttu-id="348f0-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="348f0-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="348f0-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="348f0-119">Debugging</span></span>](index.md)
