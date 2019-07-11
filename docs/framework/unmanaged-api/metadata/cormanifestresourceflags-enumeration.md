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
ms.openlocfilehash: 08f997e133fa6cc8769efe18e7ca06c0153f15a4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781802"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="7f335-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7f335-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="7f335-103">指出編碼的組件資訊清單中的資源的可見性。</span><span class="sxs-lookup"><span data-stu-id="7f335-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f335-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f335-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7f335-105">成員</span><span class="sxs-lookup"><span data-stu-id="7f335-105">Members</span></span>  
  
|<span data-ttu-id="7f335-106">成員</span><span class="sxs-lookup"><span data-stu-id="7f335-106">Member</span></span>|<span data-ttu-id="7f335-107">說明</span><span class="sxs-lookup"><span data-stu-id="7f335-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="7f335-108">保留的。</span><span class="sxs-lookup"><span data-stu-id="7f335-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="7f335-109">資源是公用的。</span><span class="sxs-lookup"><span data-stu-id="7f335-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="7f335-110">資源是私人的。</span><span class="sxs-lookup"><span data-stu-id="7f335-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f335-111">需求</span><span class="sxs-lookup"><span data-stu-id="7f335-111">Requirements</span></span>  
 <span data-ttu-id="7f335-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f335-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f335-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7f335-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7f335-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f335-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f335-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f335-115">See also</span></span>

- [<span data-ttu-id="7f335-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="7f335-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
