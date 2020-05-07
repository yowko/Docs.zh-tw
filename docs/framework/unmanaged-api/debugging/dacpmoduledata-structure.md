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
ms.openlocfilehash: e10d1792a8dc0b57ddd121ec09854e8e1824cade
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860796"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="06785-102">DacpMethodData 結構</span><span class="sxs-lookup"><span data-stu-id="06785-102">DacpModuleData Structure</span></span>

<span data-ttu-id="06785-103">定義模組執行時間資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="06785-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="06785-104">語法</span><span class="sxs-lookup"><span data-stu-id="06785-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="06785-105">成員</span><span class="sxs-lookup"><span data-stu-id="06785-105">Members</span></span>

| <span data-ttu-id="06785-106">member</span><span class="sxs-lookup"><span data-stu-id="06785-106">Member</span></span>    | <span data-ttu-id="06785-107">描述</span><span class="sxs-lookup"><span data-stu-id="06785-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="06785-108">模組物件的位址。</span><span class="sxs-lookup"><span data-stu-id="06785-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="06785-109">可移植執行檔（PE）的指標。</span><span class="sxs-lookup"><span data-stu-id="06785-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="06785-110">載入影像基底的位址。</span><span class="sxs-lookup"><span data-stu-id="06785-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="06785-111">執行時間所使用之其他模組資訊的承載緩衝區。</span><span class="sxs-lookup"><span data-stu-id="06785-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="06785-112">備註</span><span class="sxs-lookup"><span data-stu-id="06785-112">Remarks</span></span>

<span data-ttu-id="06785-113">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="06785-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="06785-114">若要使用它，請依照上面的指定定義結構。</span><span class="sxs-lookup"><span data-stu-id="06785-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="06785-115">需求</span><span class="sxs-lookup"><span data-stu-id="06785-115">Requirements</span></span>
<span data-ttu-id="06785-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06785-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="06785-117">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="06785-117">**Header:** None</span></span>  
<span data-ttu-id="06785-118">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="06785-118">**Library:** None</span></span>  
<span data-ttu-id="06785-119">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="06785-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="06785-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="06785-120">See also</span></span>

- [<span data-ttu-id="06785-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="06785-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="06785-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="06785-122">Debugging Structures</span></span>](debugging-structures.md)
