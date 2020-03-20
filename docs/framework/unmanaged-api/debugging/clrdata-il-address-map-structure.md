---
title: CLRDATA_IL_ADDRESS_MAP 結構
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179368"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="e323d-102">CLRDATA_IL_ADDRESS_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="e323d-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="e323d-103">定義 IL 以解決映射。</span><span class="sxs-lookup"><span data-stu-id="e323d-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e323d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e323d-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="e323d-105">成員</span><span class="sxs-lookup"><span data-stu-id="e323d-105">Members</span></span>

| <span data-ttu-id="e323d-106">member</span><span class="sxs-lookup"><span data-stu-id="e323d-106">Member</span></span>         | <span data-ttu-id="e323d-107">描述</span><span class="sxs-lookup"><span data-stu-id="e323d-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="e323d-108">包含位址範圍的 IL 偏移量</span><span class="sxs-lookup"><span data-stu-id="e323d-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="e323d-109">範圍的起始位址。</span><span class="sxs-lookup"><span data-stu-id="e323d-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="e323d-110">範圍的結束位址。</span><span class="sxs-lookup"><span data-stu-id="e323d-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="e323d-111">資料的類型。</span><span class="sxs-lookup"><span data-stu-id="e323d-111">The type of the data.</span></span> <span data-ttu-id="e323d-112">當前未使用此值</span><span class="sxs-lookup"><span data-stu-id="e323d-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="e323d-113">備註</span><span class="sxs-lookup"><span data-stu-id="e323d-113">Remarks</span></span>

<span data-ttu-id="e323d-114">此結構位於運行時內，不會通過任何標頭或庫檔公開。</span><span class="sxs-lookup"><span data-stu-id="e323d-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e323d-115">要使用它，請定義上面指定的結構，其中`CLRDATA_ADDRESS`是 64 位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e323d-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="e323d-116">需求</span><span class="sxs-lookup"><span data-stu-id="e323d-116">Requirements</span></span>

<span data-ttu-id="e323d-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e323d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e323d-118">**標題：** 沒有</span><span class="sxs-lookup"><span data-stu-id="e323d-118">**Header:** None</span></span>  
<span data-ttu-id="e323d-119">**庫：** 無 **.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e323d-119">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e323d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e323d-120">See also</span></span>

- [<span data-ttu-id="e323d-121">CLRDataSource 類型枚舉</span><span class="sxs-lookup"><span data-stu-id="e323d-121">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e323d-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="e323d-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="e323d-123">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="e323d-123">Debugging Structures</span></span>](debugging-structures.md)
