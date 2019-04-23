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
ms.openlocfilehash: 204f04b1ed1ea293639e0b9826f7e0ce6f384763
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198539"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="d2833-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="d2833-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="d2833-103">指出編碼的組件資訊清單中的資源的可見性。</span><span class="sxs-lookup"><span data-stu-id="d2833-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2833-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2833-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d2833-105">成員</span><span class="sxs-lookup"><span data-stu-id="d2833-105">Members</span></span>  
  
|<span data-ttu-id="d2833-106">成員</span><span class="sxs-lookup"><span data-stu-id="d2833-106">Member</span></span>|<span data-ttu-id="d2833-107">描述</span><span class="sxs-lookup"><span data-stu-id="d2833-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="d2833-108">保留的。</span><span class="sxs-lookup"><span data-stu-id="d2833-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="d2833-109">資源是公用的。</span><span class="sxs-lookup"><span data-stu-id="d2833-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="d2833-110">資源是私人的。</span><span class="sxs-lookup"><span data-stu-id="d2833-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2833-111">需求</span><span class="sxs-lookup"><span data-stu-id="d2833-111">Requirements</span></span>  
 <span data-ttu-id="d2833-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2833-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2833-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d2833-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d2833-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2833-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2833-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2833-115">See also</span></span>

- [<span data-ttu-id="d2833-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="d2833-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
