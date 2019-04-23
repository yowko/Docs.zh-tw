---
title: DacpGetModuleAddress Structure
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cbea6c0562c68ae5d18247dc97bc53eb9dfbfd7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104101"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="af54f-102">DacpGetModuleAddress Structure</span><span class="sxs-lookup"><span data-stu-id="af54f-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="af54f-103">定義模組位址要求的容器。</span><span class="sxs-lookup"><span data-stu-id="af54f-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="af54f-104">語法</span><span class="sxs-lookup"><span data-stu-id="af54f-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="af54f-105">成員</span><span class="sxs-lookup"><span data-stu-id="af54f-105">Members</span></span>

| <span data-ttu-id="af54f-106">成員</span><span class="sxs-lookup"><span data-stu-id="af54f-106">Member</span></span>      | <span data-ttu-id="af54f-107">描述</span><span class="sxs-lookup"><span data-stu-id="af54f-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="af54f-108">要模組的指標。</span><span class="sxs-lookup"><span data-stu-id="af54f-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="af54f-109">方法</span><span class="sxs-lookup"><span data-stu-id="af54f-109">Methods</span></span>

| <span data-ttu-id="af54f-110">方法</span><span class="sxs-lookup"><span data-stu-id="af54f-110">Method</span></span>                                                                                               | <span data-ttu-id="af54f-111">描述</span><span class="sxs-lookup"><span data-stu-id="af54f-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="af54f-112">要求</span><span class="sxs-lookup"><span data-stu-id="af54f-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="af54f-113">會執行要求，以填入指定的執行階段結構中的結構。</span><span class="sxs-lookup"><span data-stu-id="af54f-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="af54f-114">備註</span><span class="sxs-lookup"><span data-stu-id="af54f-114">Remarks</span></span>

<span data-ttu-id="af54f-115">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="af54f-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="af54f-116">若要使用它，將結構定義成指定上述其中`CLRDATA_ADDRESS`是 64 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="af54f-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="af54f-117">需求</span><span class="sxs-lookup"><span data-stu-id="af54f-117">Requirements</span></span>
<span data-ttu-id="af54f-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af54f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="af54f-119">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="af54f-119">**Header:** None</span></span>  
<span data-ttu-id="af54f-120">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="af54f-120">**Library:** None</span></span>  
<span data-ttu-id="af54f-121">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="af54f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="af54f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af54f-122">See also</span></span>

- [<span data-ttu-id="af54f-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="af54f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="af54f-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="af54f-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
