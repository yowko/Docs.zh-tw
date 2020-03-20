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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179193"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="b5deb-102">DacpMethodData 結構</span><span class="sxs-lookup"><span data-stu-id="b5deb-102">DacpModuleData Structure</span></span>

<span data-ttu-id="b5deb-103">為模組的運行時資訊定義傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b5deb-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b5deb-104">語法</span><span class="sxs-lookup"><span data-stu-id="b5deb-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="b5deb-105">成員</span><span class="sxs-lookup"><span data-stu-id="b5deb-105">Members</span></span>

| <span data-ttu-id="b5deb-106">member</span><span class="sxs-lookup"><span data-stu-id="b5deb-106">Member</span></span>    | <span data-ttu-id="b5deb-107">描述</span><span class="sxs-lookup"><span data-stu-id="b5deb-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="b5deb-108">模組物件的位址。</span><span class="sxs-lookup"><span data-stu-id="b5deb-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="b5deb-109">指向可攜式可執行檔 （PE） 檔的指標。</span><span class="sxs-lookup"><span data-stu-id="b5deb-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="b5deb-110">載入圖像的基的位址。</span><span class="sxs-lookup"><span data-stu-id="b5deb-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="b5deb-111">用於運行時使用的其他模組資訊的有效負載緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b5deb-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b5deb-112">備註</span><span class="sxs-lookup"><span data-stu-id="b5deb-112">Remarks</span></span>

<span data-ttu-id="b5deb-113">此結構位於運行時內，不會通過任何標頭或庫檔公開。</span><span class="sxs-lookup"><span data-stu-id="b5deb-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b5deb-114">要使用它，請定義上面指定的結構。</span><span class="sxs-lookup"><span data-stu-id="b5deb-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5deb-115">需求</span><span class="sxs-lookup"><span data-stu-id="b5deb-115">Requirements</span></span>
<span data-ttu-id="b5deb-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5deb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b5deb-117">**標題：** 沒有</span><span class="sxs-lookup"><span data-stu-id="b5deb-117">**Header:** None</span></span>  
<span data-ttu-id="b5deb-118">**庫：** 沒有</span><span class="sxs-lookup"><span data-stu-id="b5deb-118">**Library:** None</span></span>  
<span data-ttu-id="b5deb-119">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b5deb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b5deb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5deb-120">See also</span></span>

- [<span data-ttu-id="b5deb-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="b5deb-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="b5deb-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="b5deb-122">Debugging Structures</span></span>](debugging-structures.md)
