---
title: DacpReJitData Structure
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a2850add9acb2f7c5297ac6956e349c9277be291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122794"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="cceb5-102">DacpReJitData Structure</span><span class="sxs-lookup"><span data-stu-id="cceb5-102">DacpReJitData Structure</span></span>

<span data-ttu-id="cceb5-103">定義指定的程式碼剖析工具檢測方法的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="cceb5-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="cceb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="cceb5-104">Syntax</span></span>

```
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="cceb5-105">成員</span><span class="sxs-lookup"><span data-stu-id="cceb5-105">Members</span></span>

| <span data-ttu-id="cceb5-106">成員</span><span class="sxs-lookup"><span data-stu-id="cceb5-106">Member</span></span>           | <span data-ttu-id="cceb5-107">描述</span><span class="sxs-lookup"><span data-stu-id="cceb5-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="cceb5-108">ReJit 修訂編號的方法。</span><span class="sxs-lookup"><span data-stu-id="cceb5-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="cceb5-109">旗標，指出指定之版本的方法的 ReJit 檢測的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="cceb5-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="cceb5-110">方法的 rejitted 實作基底地址。</span><span class="sxs-lookup"><span data-stu-id="cceb5-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="cceb5-111">備註</span><span class="sxs-lookup"><span data-stu-id="cceb5-111">Remarks</span></span>

<span data-ttu-id="cceb5-112">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="cceb5-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="cceb5-113">若要使用它，定義如上述所指定的結構。</span><span class="sxs-lookup"><span data-stu-id="cceb5-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="cceb5-114">結構也必須定義使用`ms_struct`封裝，如果未使用的 Microsoft 編譯器。</span><span class="sxs-lookup"><span data-stu-id="cceb5-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="cceb5-115">需求</span><span class="sxs-lookup"><span data-stu-id="cceb5-115">Requirements</span></span>
<span data-ttu-id="cceb5-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cceb5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="cceb5-117">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="cceb5-117">**Header:** None</span></span>  
<span data-ttu-id="cceb5-118">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="cceb5-118">**Library:** None</span></span>  
<span data-ttu-id="cceb5-119">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cceb5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cceb5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cceb5-120">See also</span></span>

- [<span data-ttu-id="cceb5-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="cceb5-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="cceb5-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="cceb5-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
