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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860834"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="77eef-102">DacpGetModuleAddress 結構</span><span class="sxs-lookup"><span data-stu-id="77eef-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="77eef-103">定義模組位址要求的容器。</span><span class="sxs-lookup"><span data-stu-id="77eef-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="77eef-104">語法</span><span class="sxs-lookup"><span data-stu-id="77eef-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="77eef-105">成員</span><span class="sxs-lookup"><span data-stu-id="77eef-105">Members</span></span>

| <span data-ttu-id="77eef-106">member</span><span class="sxs-lookup"><span data-stu-id="77eef-106">Member</span></span>      | <span data-ttu-id="77eef-107">描述</span><span class="sxs-lookup"><span data-stu-id="77eef-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="77eef-108">模組的指標。</span><span class="sxs-lookup"><span data-stu-id="77eef-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="77eef-109">方法</span><span class="sxs-lookup"><span data-stu-id="77eef-109">Methods</span></span>

| <span data-ttu-id="77eef-110">方法</span><span class="sxs-lookup"><span data-stu-id="77eef-110">Method</span></span>                                                                                               | <span data-ttu-id="77eef-111">描述</span><span class="sxs-lookup"><span data-stu-id="77eef-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="77eef-112">要求</span><span class="sxs-lookup"><span data-stu-id="77eef-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="77eef-113">執行要求，以從指定的執行時間結構填入結構。</span><span class="sxs-lookup"><span data-stu-id="77eef-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="77eef-114">備註</span><span class="sxs-lookup"><span data-stu-id="77eef-114">Remarks</span></span>

<span data-ttu-id="77eef-115">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="77eef-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="77eef-116">若要使用它，請定義如上所指定的結構`CLRDATA_ADDRESS` ，其中是64位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="77eef-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="77eef-117">需求</span><span class="sxs-lookup"><span data-stu-id="77eef-117">Requirements</span></span>
<span data-ttu-id="77eef-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77eef-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="77eef-119">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="77eef-119">**Header:** None</span></span>  
<span data-ttu-id="77eef-120">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="77eef-120">**Library:** None</span></span>  
<span data-ttu-id="77eef-121">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77eef-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="77eef-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="77eef-122">See also</span></span>

- [<span data-ttu-id="77eef-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="77eef-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="77eef-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="77eef-124">Debugging Structures</span></span>](debugging-structures.md)
