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
ms.openlocfilehash: 35966e25d02bd6f1a9bdd21ad4e9cc44b7bb480e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450254"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="01014-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="01014-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="01014-103">表示在組件資訊清單中編碼的資源可見度。</span><span class="sxs-lookup"><span data-stu-id="01014-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01014-104">語法</span><span class="sxs-lookup"><span data-stu-id="01014-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="01014-105">Members</span><span class="sxs-lookup"><span data-stu-id="01014-105">Members</span></span>  
  
|<span data-ttu-id="01014-106">成員</span><span class="sxs-lookup"><span data-stu-id="01014-106">Member</span></span>|<span data-ttu-id="01014-107">描述</span><span class="sxs-lookup"><span data-stu-id="01014-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="01014-108">保留。</span><span class="sxs-lookup"><span data-stu-id="01014-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="01014-109">資源是公用的。</span><span class="sxs-lookup"><span data-stu-id="01014-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="01014-110">資源是私用的。</span><span class="sxs-lookup"><span data-stu-id="01014-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01014-111">需求</span><span class="sxs-lookup"><span data-stu-id="01014-111">Requirements</span></span>  
 <span data-ttu-id="01014-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01014-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01014-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="01014-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="01014-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01014-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01014-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01014-115">See also</span></span>

- [<span data-ttu-id="01014-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="01014-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
