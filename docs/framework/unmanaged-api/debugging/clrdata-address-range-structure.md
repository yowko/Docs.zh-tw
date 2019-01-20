---
title: CLRDATA_ADDRESS_RANGE 結構
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3a8832a0eb173da00715bd0441b7efd337eae932
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416325"
---
# <a name="clrdataaddressrange-structure"></a><span data-ttu-id="6ca59-102">CLRDATA_ADDRESS_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="6ca59-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="6ca59-103">定義的位址範圍。</span><span class="sxs-lookup"><span data-stu-id="6ca59-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6ca59-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ca59-104">Syntax</span></span>

```
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="6ca59-105">成員</span><span class="sxs-lookup"><span data-stu-id="6ca59-105">Members</span></span>

| <span data-ttu-id="6ca59-106">成員</span><span class="sxs-lookup"><span data-stu-id="6ca59-106">Member</span></span>         | <span data-ttu-id="6ca59-107">描述</span><span class="sxs-lookup"><span data-stu-id="6ca59-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="6ca59-108">範圍的起始位址。</span><span class="sxs-lookup"><span data-stu-id="6ca59-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="6ca59-109">範圍結束位址。</span><span class="sxs-lookup"><span data-stu-id="6ca59-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="6ca59-110">備註</span><span class="sxs-lookup"><span data-stu-id="6ca59-110">Remarks</span></span>

<span data-ttu-id="6ca59-111">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="6ca59-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6ca59-112">若要使用它，將結構定義成指定上述其中`CLRDATA_ADDRESS`是 64 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="6ca59-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ca59-113">需求</span><span class="sxs-lookup"><span data-stu-id="6ca59-113">Requirements</span></span>

<span data-ttu-id="6ca59-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca59-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6ca59-115">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="6ca59-115">**Header:** None</span></span>  
<span data-ttu-id="6ca59-116">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="6ca59-116">**Library:** None</span></span>  
<span data-ttu-id="6ca59-117">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca59-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6ca59-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca59-118">See Also</span></span>

- [<span data-ttu-id="6ca59-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="6ca59-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="6ca59-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="6ca59-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
