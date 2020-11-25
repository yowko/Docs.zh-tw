---
title: DacpMethodData 結構
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 5d27ba2de9ff6ed184b6ddf50a517d0dae7715f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723047"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="fcf89-102">DacpMethodData 結構</span><span class="sxs-lookup"><span data-stu-id="fcf89-102">DacpModuleData Structure</span></span>

<span data-ttu-id="fcf89-103">定義模組執行時間資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fcf89-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fcf89-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcf89-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="fcf89-105">成員</span><span class="sxs-lookup"><span data-stu-id="fcf89-105">Members</span></span>

| <span data-ttu-id="fcf89-106">member</span><span class="sxs-lookup"><span data-stu-id="fcf89-106">Member</span></span>    | <span data-ttu-id="fcf89-107">描述</span><span class="sxs-lookup"><span data-stu-id="fcf89-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="fcf89-108">模組物件的位址。</span><span class="sxs-lookup"><span data-stu-id="fcf89-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="fcf89-109">可攜式可執行檔的指標， (PE) 檔。</span><span class="sxs-lookup"><span data-stu-id="fcf89-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="fcf89-110">已載入映射基底的位址。</span><span class="sxs-lookup"><span data-stu-id="fcf89-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="fcf89-111">執行時間所使用之其他模組資訊的承載緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fcf89-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="fcf89-112">備註</span><span class="sxs-lookup"><span data-stu-id="fcf89-112">Remarks</span></span>

<span data-ttu-id="fcf89-113">此結構存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="fcf89-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fcf89-114">若要使用它，請依照上述指定的方式定義結構。</span><span class="sxs-lookup"><span data-stu-id="fcf89-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcf89-115">需求</span><span class="sxs-lookup"><span data-stu-id="fcf89-115">Requirements</span></span>

<span data-ttu-id="fcf89-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf89-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fcf89-117">**標頭：** 沒有</span><span class="sxs-lookup"><span data-stu-id="fcf89-117">**Header:** None</span></span>  
<span data-ttu-id="fcf89-118">連結 **庫：** 沒有</span><span class="sxs-lookup"><span data-stu-id="fcf89-118">**Library:** None</span></span>  
<span data-ttu-id="fcf89-119">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf89-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fcf89-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcf89-120">See also</span></span>

- [<span data-ttu-id="fcf89-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="fcf89-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="fcf89-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="fcf89-122">Debugging Structures</span></span>](debugging-structures.md)
