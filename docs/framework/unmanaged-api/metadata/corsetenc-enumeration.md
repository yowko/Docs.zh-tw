---
title: CorSetENC 列舉
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432768"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="da7d4-102">CorSetENC 列舉</span><span class="sxs-lookup"><span data-stu-id="da7d4-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="da7d4-103">包含值，可用來在中繼資料產生期間影響行為。</span><span class="sxs-lookup"><span data-stu-id="da7d4-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="da7d4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="da7d4-105">Members</span><span class="sxs-lookup"><span data-stu-id="da7d4-105">Members</span></span>  
  
|<span data-ttu-id="da7d4-106">成員</span><span class="sxs-lookup"><span data-stu-id="da7d4-106">Member</span></span>|<span data-ttu-id="da7d4-107">描述</span><span class="sxs-lookup"><span data-stu-id="da7d4-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="da7d4-108">已經過時：</span><span class="sxs-lookup"><span data-stu-id="da7d4-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="da7d4-109">已經過時：</span><span class="sxs-lookup"><span data-stu-id="da7d4-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="da7d4-110">表示中繼資料可以更新，而無法移動權杖。</span><span class="sxs-lookup"><span data-stu-id="da7d4-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="da7d4-111">表示權杖可在更新期間移動。</span><span class="sxs-lookup"><span data-stu-id="da7d4-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="da7d4-112">指出更新只能包含新增專案。</span><span class="sxs-lookup"><span data-stu-id="da7d4-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="da7d4-113">無法移動權杖。</span><span class="sxs-lookup"><span data-stu-id="da7d4-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="da7d4-114">表示編譯是累加的。</span><span class="sxs-lookup"><span data-stu-id="da7d4-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="da7d4-115">指出只應儲存已變更的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="da7d4-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="da7d4-116">包括 `MDUpdateENC`、`MDUpdateFull` 和 `MDUpdateIncremental`。</span><span class="sxs-lookup"><span data-stu-id="da7d4-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da7d4-117">需求</span><span class="sxs-lookup"><span data-stu-id="da7d4-117">Requirements</span></span>  
 <span data-ttu-id="da7d4-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da7d4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7d4-119">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="da7d4-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="da7d4-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da7d4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7d4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da7d4-121">See also</span></span>

- [<span data-ttu-id="da7d4-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="da7d4-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
