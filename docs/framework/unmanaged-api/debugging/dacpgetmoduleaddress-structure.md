---
title: DacpGetModuleAddress 結構
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
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789197"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="892cd-102">DacpGetModuleAddress 結構</span><span class="sxs-lookup"><span data-stu-id="892cd-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="892cd-103">定義模組位址要求的容器。</span><span class="sxs-lookup"><span data-stu-id="892cd-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="892cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="892cd-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="892cd-105">Members</span><span class="sxs-lookup"><span data-stu-id="892cd-105">Members</span></span>

| <span data-ttu-id="892cd-106">成員</span><span class="sxs-lookup"><span data-stu-id="892cd-106">Member</span></span>      | <span data-ttu-id="892cd-107">描述</span><span class="sxs-lookup"><span data-stu-id="892cd-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="892cd-108">模組的指標。</span><span class="sxs-lookup"><span data-stu-id="892cd-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="892cd-109">方法</span><span class="sxs-lookup"><span data-stu-id="892cd-109">Methods</span></span>

| <span data-ttu-id="892cd-110">方法</span><span class="sxs-lookup"><span data-stu-id="892cd-110">Method</span></span>                                                                                               | <span data-ttu-id="892cd-111">描述</span><span class="sxs-lookup"><span data-stu-id="892cd-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="892cd-112">要求</span><span class="sxs-lookup"><span data-stu-id="892cd-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="892cd-113">執行要求，以從指定的執行時間結構填入結構。</span><span class="sxs-lookup"><span data-stu-id="892cd-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="892cd-114">備註</span><span class="sxs-lookup"><span data-stu-id="892cd-114">Remarks</span></span>

<span data-ttu-id="892cd-115">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="892cd-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="892cd-116">若要使用它，請定義如上所指定的結構，其中 `CLRDATA_ADDRESS` 是64位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="892cd-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="892cd-117">需求</span><span class="sxs-lookup"><span data-stu-id="892cd-117">Requirements</span></span>
<span data-ttu-id="892cd-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="892cd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="892cd-119">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="892cd-119">**Header:** None</span></span>  
<span data-ttu-id="892cd-120">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="892cd-120">**Library:** None</span></span>  
<span data-ttu-id="892cd-121">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="892cd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="892cd-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="892cd-122">See also</span></span>

- [<span data-ttu-id="892cd-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="892cd-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="892cd-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="892cd-124">Debugging Structures</span></span>](debugging-structures.md)
