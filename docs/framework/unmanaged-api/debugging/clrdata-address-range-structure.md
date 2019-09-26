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
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274303"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="f5597-102">CLRDATA_ADDRESS_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="f5597-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="f5597-103">定義位址範圍。</span><span class="sxs-lookup"><span data-stu-id="f5597-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f5597-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5597-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="f5597-105">成員</span><span class="sxs-lookup"><span data-stu-id="f5597-105">Members</span></span>

| <span data-ttu-id="f5597-106">成員</span><span class="sxs-lookup"><span data-stu-id="f5597-106">Member</span></span>         | <span data-ttu-id="f5597-107">描述</span><span class="sxs-lookup"><span data-stu-id="f5597-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="f5597-108">範圍的開始位址。</span><span class="sxs-lookup"><span data-stu-id="f5597-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="f5597-109">範圍的結束位址。</span><span class="sxs-lookup"><span data-stu-id="f5597-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="f5597-110">備註</span><span class="sxs-lookup"><span data-stu-id="f5597-110">Remarks</span></span>

<span data-ttu-id="f5597-111">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="f5597-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f5597-112">若要使用它，請定義如上所指定的結構`CLRDATA_ADDRESS` ，其中是64位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="f5597-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5597-113">需求</span><span class="sxs-lookup"><span data-stu-id="f5597-113">Requirements</span></span>

<span data-ttu-id="f5597-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5597-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f5597-115">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="f5597-115">**Header:** None</span></span>  
<span data-ttu-id="f5597-116">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="f5597-116">**Library:** None</span></span>  
<span data-ttu-id="f5597-117">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5597-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f5597-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5597-118">See also</span></span>

- [<span data-ttu-id="f5597-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="f5597-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="f5597-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="f5597-120">Debugging Structures</span></span>](debugging-structures.md)
