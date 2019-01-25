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
ms.openlocfilehash: c0a12ab638adfccfb6406aa495bd3568911ee969
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619775"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="95f4b-102">DacpGetModuleAddress Structure</span><span class="sxs-lookup"><span data-stu-id="95f4b-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="95f4b-103">定義模組位址要求的容器。</span><span class="sxs-lookup"><span data-stu-id="95f4b-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="95f4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="95f4b-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="95f4b-105">成員</span><span class="sxs-lookup"><span data-stu-id="95f4b-105">Members</span></span>

| <span data-ttu-id="95f4b-106">成員</span><span class="sxs-lookup"><span data-stu-id="95f4b-106">Member</span></span>      | <span data-ttu-id="95f4b-107">描述</span><span class="sxs-lookup"><span data-stu-id="95f4b-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="95f4b-108">要模組的指標。</span><span class="sxs-lookup"><span data-stu-id="95f4b-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="95f4b-109">方法</span><span class="sxs-lookup"><span data-stu-id="95f4b-109">Methods</span></span>

| <span data-ttu-id="95f4b-110">方法</span><span class="sxs-lookup"><span data-stu-id="95f4b-110">Method</span></span>                                                                                               | <span data-ttu-id="95f4b-111">描述</span><span class="sxs-lookup"><span data-stu-id="95f4b-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="95f4b-112">要求</span><span class="sxs-lookup"><span data-stu-id="95f4b-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="95f4b-113">會執行要求，以填入指定的執行階段結構中的結構。</span><span class="sxs-lookup"><span data-stu-id="95f4b-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="95f4b-114">備註</span><span class="sxs-lookup"><span data-stu-id="95f4b-114">Remarks</span></span>

<span data-ttu-id="95f4b-115">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="95f4b-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="95f4b-116">若要使用它，將結構定義成指定上述其中`CLRDATA_ADDRESS`是 64 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="95f4b-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="95f4b-117">需求</span><span class="sxs-lookup"><span data-stu-id="95f4b-117">Requirements</span></span>
<span data-ttu-id="95f4b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95f4b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="95f4b-119">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="95f4b-119">**Header:** None</span></span>  
<span data-ttu-id="95f4b-120">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="95f4b-120">**Library:** None</span></span>  
<span data-ttu-id="95f4b-121">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="95f4b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="95f4b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f4b-122">See also</span></span>
- [<span data-ttu-id="95f4b-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="95f4b-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="95f4b-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="95f4b-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
