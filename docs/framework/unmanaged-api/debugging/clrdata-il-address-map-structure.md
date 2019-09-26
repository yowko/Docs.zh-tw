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
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274298"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="a68c7-102">CLRDATA_IL_ADDRESS_MAP 結構</span><span class="sxs-lookup"><span data-stu-id="a68c7-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="a68c7-103">定義要定址對應的 IL。</span><span class="sxs-lookup"><span data-stu-id="a68c7-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a68c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="a68c7-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="a68c7-105">成員</span><span class="sxs-lookup"><span data-stu-id="a68c7-105">Members</span></span>

| <span data-ttu-id="a68c7-106">成員</span><span class="sxs-lookup"><span data-stu-id="a68c7-106">Member</span></span>         | <span data-ttu-id="a68c7-107">描述</span><span class="sxs-lookup"><span data-stu-id="a68c7-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="a68c7-108">包含之位址範圍的 IL 位移</span><span class="sxs-lookup"><span data-stu-id="a68c7-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="a68c7-109">範圍的開始位址。</span><span class="sxs-lookup"><span data-stu-id="a68c7-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="a68c7-110">範圍的結束位址。</span><span class="sxs-lookup"><span data-stu-id="a68c7-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="a68c7-111">資料的類型。</span><span class="sxs-lookup"><span data-stu-id="a68c7-111">The type of the data.</span></span> <span data-ttu-id="a68c7-112">目前未使用這個值</span><span class="sxs-lookup"><span data-stu-id="a68c7-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="a68c7-113">備註</span><span class="sxs-lookup"><span data-stu-id="a68c7-113">Remarks</span></span>

<span data-ttu-id="a68c7-114">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="a68c7-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a68c7-115">若要使用它，請定義如上所指定的結構`CLRDATA_ADDRESS` ，其中是64位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="a68c7-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a68c7-116">需求</span><span class="sxs-lookup"><span data-stu-id="a68c7-116">Requirements</span></span>

<span data-ttu-id="a68c7-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a68c7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a68c7-118">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="a68c7-118">**Header:** None</span></span>  
<span data-ttu-id="a68c7-119">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="a68c7-119">**Library:** None</span></span>   
<span data-ttu-id="a68c7-120">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a68c7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a68c7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a68c7-121">See also</span></span>

- [<span data-ttu-id="a68c7-122">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="a68c7-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a68c7-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="a68c7-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="a68c7-124">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="a68c7-124">Debugging Structures</span></span>](debugging-structures.md)
