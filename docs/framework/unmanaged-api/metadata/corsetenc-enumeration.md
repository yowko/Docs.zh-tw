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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fd903cb4a9ce664b7a1c958a3fef0c639d6845d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045314"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="855e3-102">CorSetENC 列舉</span><span class="sxs-lookup"><span data-stu-id="855e3-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="855e3-103">包含值，可用來在中繼資料產生期間影響行為。</span><span class="sxs-lookup"><span data-stu-id="855e3-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="855e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="855e3-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="855e3-105">成員</span><span class="sxs-lookup"><span data-stu-id="855e3-105">Members</span></span>  
  
|<span data-ttu-id="855e3-106">成員</span><span class="sxs-lookup"><span data-stu-id="855e3-106">Member</span></span>|<span data-ttu-id="855e3-107">描述</span><span class="sxs-lookup"><span data-stu-id="855e3-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="855e3-108">已過時。</span><span class="sxs-lookup"><span data-stu-id="855e3-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="855e3-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="855e3-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="855e3-110">表示可以更新中繼資料，而不移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="855e3-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="855e3-111">表示可以在更新過程中移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="855e3-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="855e3-112">指出，更新可以只包含加入項目。</span><span class="sxs-lookup"><span data-stu-id="855e3-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="855e3-113">無法移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="855e3-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="855e3-114">表示累加編譯。</span><span class="sxs-lookup"><span data-stu-id="855e3-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="855e3-115">表示應該儲存，只有已變更的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="855e3-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="855e3-116">包含`MDUpdateENC`，`MDUpdateFull`和`MDUpdateIncremental`。</span><span class="sxs-lookup"><span data-stu-id="855e3-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="855e3-117">需求</span><span class="sxs-lookup"><span data-stu-id="855e3-117">Requirements</span></span>  
 <span data-ttu-id="855e3-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="855e3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855e3-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="855e3-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="855e3-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855e3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855e3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="855e3-121">See also</span></span>

- [<span data-ttu-id="855e3-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="855e3-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
