---
title: CorDebugMDAFlags 列舉
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: 1bb99503481d917d41ae00a5ef73c8fa59e2a999
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696449"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="8b55e-102">CorDebugMDAFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="8b55e-102">CorDebugMDAFlags Enumeration</span></span>

<span data-ttu-id="8b55e-103">指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="8b55e-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b55e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b55e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8b55e-105">成員</span><span class="sxs-lookup"><span data-stu-id="8b55e-105">Members</span></span>  
  
|<span data-ttu-id="8b55e-106">member</span><span class="sxs-lookup"><span data-stu-id="8b55e-106">Member</span></span>|<span data-ttu-id="8b55e-107">描述</span><span class="sxs-lookup"><span data-stu-id="8b55e-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="8b55e-108">引發 mda 的執行緒已在引發 MDA 之後跳過。</span><span class="sxs-lookup"><span data-stu-id="8b55e-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b55e-109">備註</span><span class="sxs-lookup"><span data-stu-id="8b55e-109">Remarks</span></span>  

 <span data-ttu-id="8b55e-110">當呼叫堆疊不再描述 MDA 最初引發的位置時，執行緒會被視為已 *落後*。</span><span class="sxs-lookup"><span data-stu-id="8b55e-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="8b55e-111">這是因執行緒在結束時執行無效作業而發生的異常情況。</span><span class="sxs-lookup"><span data-stu-id="8b55e-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b55e-112">需求</span><span class="sxs-lookup"><span data-stu-id="8b55e-112">Requirements</span></span>  

 <span data-ttu-id="8b55e-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b55e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b55e-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b55e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b55e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b55e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b55e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b55e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b55e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b55e-117">See also</span></span>

- [<span data-ttu-id="8b55e-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="8b55e-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
