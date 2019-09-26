---
title: CLRDataSourceType 列舉
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274100"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="44a47-102">CLRDataSourceType 列舉</span><span class="sxs-lookup"><span data-stu-id="44a47-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="44a47-103">提供 CLRDATA_IL_ADDRESS_MAP 結構所使用的值。</span><span class="sxs-lookup"><span data-stu-id="44a47-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="44a47-104">語法</span><span class="sxs-lookup"><span data-stu-id="44a47-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="44a47-105">成員</span><span class="sxs-lookup"><span data-stu-id="44a47-105">Members</span></span>

| <span data-ttu-id="44a47-106">成員</span><span class="sxs-lookup"><span data-stu-id="44a47-106">Member</span></span>                        | <span data-ttu-id="44a47-107">描述</span><span class="sxs-lookup"><span data-stu-id="44a47-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="44a47-108">表示沒有其他適用的</span><span class="sxs-lookup"><span data-stu-id="44a47-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="44a47-109">備註</span><span class="sxs-lookup"><span data-stu-id="44a47-109">Remarks</span></span>

<span data-ttu-id="44a47-110">此列舉會存留在執行時間內，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="44a47-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="44a47-111">若要使用它，請在您的程式碼中定義上述定義的列舉。</span><span class="sxs-lookup"><span data-stu-id="44a47-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="44a47-112">這也是的別名`CLRDATA_ENUM` ，如[一般資料類型](../common-data-types-unmanaged-api-reference.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="44a47-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="44a47-113">需求</span><span class="sxs-lookup"><span data-stu-id="44a47-113">Requirements</span></span>

<span data-ttu-id="44a47-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44a47-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="44a47-115">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="44a47-115">**Header:** None</span></span>  
<span data-ttu-id="44a47-116">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="44a47-116">**Library:** None</span></span>  
<span data-ttu-id="44a47-117">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="44a47-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="44a47-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44a47-118">See also</span></span>

- [<span data-ttu-id="44a47-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="44a47-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="44a47-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="44a47-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
