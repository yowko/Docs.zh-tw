---
title: "CorSetENC 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="b1b76-102">CorSetENC 列舉</span><span class="sxs-lookup"><span data-stu-id="b1b76-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="b1b76-103">包含值，可用來在中繼資料產生期間影響行為。</span><span class="sxs-lookup"><span data-stu-id="b1b76-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b76-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1b76-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b1b76-105">成員</span><span class="sxs-lookup"><span data-stu-id="b1b76-105">Members</span></span>  
  
|<span data-ttu-id="b1b76-106">成員</span><span class="sxs-lookup"><span data-stu-id="b1b76-106">Member</span></span>|<span data-ttu-id="b1b76-107">說明</span><span class="sxs-lookup"><span data-stu-id="b1b76-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="b1b76-108">已過時。</span><span class="sxs-lookup"><span data-stu-id="b1b76-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="b1b76-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="b1b76-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="b1b76-110">表示可更新的中繼資料，而不能移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1b76-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="b1b76-111">表示可以在更新過程中移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1b76-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="b1b76-112">表示更新可包含僅的新增項目。</span><span class="sxs-lookup"><span data-stu-id="b1b76-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="b1b76-113">無法移動語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1b76-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="b1b76-114">表示編譯是累加的。</span><span class="sxs-lookup"><span data-stu-id="b1b76-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="b1b76-115">表示應該儲存，只有變更的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b1b76-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="b1b76-116">包含`MDUpdateENC`，`MDUpdateFull`和`MDUpdateIncremental`。</span><span class="sxs-lookup"><span data-stu-id="b1b76-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1b76-117">需求</span><span class="sxs-lookup"><span data-stu-id="b1b76-117">Requirements</span></span>  
 <span data-ttu-id="b1b76-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1b76-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b76-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b1b76-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b1b76-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b76-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b76-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1b76-121">See Also</span></span>  
 [<span data-ttu-id="b1b76-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="b1b76-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
