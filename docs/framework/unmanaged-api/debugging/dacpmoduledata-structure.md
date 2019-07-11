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
ms.openlocfilehash: 2e27082ba4c35bc10eb65139b2af6c81c10d79a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739117"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="db974-102">DacpMethodData 結構</span><span class="sxs-lookup"><span data-stu-id="db974-102">DacpModuleData Structure</span></span>

<span data-ttu-id="db974-103">定義模組的執行階段資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="db974-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="db974-104">語法</span><span class="sxs-lookup"><span data-stu-id="db974-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="db974-105">成員</span><span class="sxs-lookup"><span data-stu-id="db974-105">Members</span></span>

| <span data-ttu-id="db974-106">成員</span><span class="sxs-lookup"><span data-stu-id="db974-106">Member</span></span>    | <span data-ttu-id="db974-107">描述</span><span class="sxs-lookup"><span data-stu-id="db974-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="db974-108">模組物件的位址。</span><span class="sxs-lookup"><span data-stu-id="db974-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="db974-109">可攜式執行檔 (PE) 指標。</span><span class="sxs-lookup"><span data-stu-id="db974-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="db974-110">載入的映像的地址的基底。</span><span class="sxs-lookup"><span data-stu-id="db974-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="db974-111">執行階段所使用的其他模組資訊內容緩衝區。</span><span class="sxs-lookup"><span data-stu-id="db974-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="db974-112">備註</span><span class="sxs-lookup"><span data-stu-id="db974-112">Remarks</span></span>

<span data-ttu-id="db974-113">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="db974-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="db974-114">若要使用它，定義如上述所指定的結構。</span><span class="sxs-lookup"><span data-stu-id="db974-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="db974-115">需求</span><span class="sxs-lookup"><span data-stu-id="db974-115">Requirements</span></span>
<span data-ttu-id="db974-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db974-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="db974-117">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="db974-117">**Header:** None</span></span>  
<span data-ttu-id="db974-118">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="db974-118">**Library:** None</span></span>  
<span data-ttu-id="db974-119">**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="db974-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="db974-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db974-120">See also</span></span>

- [<span data-ttu-id="db974-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="db974-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="db974-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="db974-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
