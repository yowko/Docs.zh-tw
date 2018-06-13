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
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442783"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="e0883-102">CorSetENC 列舉</span><span class="sxs-lookup"><span data-stu-id="e0883-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="e0883-103">包含值，可用來在中繼資料產生期間影響行為。</span><span class="sxs-lookup"><span data-stu-id="e0883-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0883-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0883-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e0883-105">成員</span><span class="sxs-lookup"><span data-stu-id="e0883-105">Members</span></span>  
  
|<span data-ttu-id="e0883-106">成員</span><span class="sxs-lookup"><span data-stu-id="e0883-106">Member</span></span>|<span data-ttu-id="e0883-107">描述</span><span class="sxs-lookup"><span data-stu-id="e0883-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="e0883-108">已過時。</span><span class="sxs-lookup"><span data-stu-id="e0883-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="e0883-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="e0883-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="e0883-110">表示可更新的中繼資料，而不能移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e0883-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="e0883-111">表示可以在更新過程中移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e0883-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="e0883-112">表示更新可包含僅的新增項目。</span><span class="sxs-lookup"><span data-stu-id="e0883-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="e0883-113">無法移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e0883-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="e0883-114">表示編譯是累加的。</span><span class="sxs-lookup"><span data-stu-id="e0883-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="e0883-115">表示應該儲存，只有變更的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e0883-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="e0883-116">包含`MDUpdateENC`，`MDUpdateFull`和`MDUpdateIncremental`。</span><span class="sxs-lookup"><span data-stu-id="e0883-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0883-117">需求</span><span class="sxs-lookup"><span data-stu-id="e0883-117">Requirements</span></span>  
 <span data-ttu-id="e0883-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0883-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0883-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e0883-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e0883-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0883-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0883-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0883-121">See Also</span></span>  
 [<span data-ttu-id="e0883-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e0883-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
