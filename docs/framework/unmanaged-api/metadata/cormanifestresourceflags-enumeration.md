---
title: CorManifestResourceFlags 列舉
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21cce26c94d26f6c079fca644a31bf83cd1a6432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440706"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="0cb0c-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="0cb0c-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="0cb0c-103">表示資源的組件資訊清單中編碼的可見性。</span><span class="sxs-lookup"><span data-stu-id="0cb0c-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cb0c-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0cb0c-105">成員</span><span class="sxs-lookup"><span data-stu-id="0cb0c-105">Members</span></span>  
  
|<span data-ttu-id="0cb0c-106">成員</span><span class="sxs-lookup"><span data-stu-id="0cb0c-106">Member</span></span>|<span data-ttu-id="0cb0c-107">描述</span><span class="sxs-lookup"><span data-stu-id="0cb0c-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="0cb0c-108">保留的。</span><span class="sxs-lookup"><span data-stu-id="0cb0c-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="0cb0c-109">資源為公用。</span><span class="sxs-lookup"><span data-stu-id="0cb0c-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="0cb0c-110">資源是私用。</span><span class="sxs-lookup"><span data-stu-id="0cb0c-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0cb0c-111">需求</span><span class="sxs-lookup"><span data-stu-id="0cb0c-111">Requirements</span></span>  
 <span data-ttu-id="0cb0c-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb0c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb0c-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0cb0c-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0cb0c-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb0c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cb0c-115">See Also</span></span>  
 [<span data-ttu-id="0cb0c-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="0cb0c-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
