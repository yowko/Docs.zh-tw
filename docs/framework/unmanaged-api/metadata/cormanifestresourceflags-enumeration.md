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
ms.openlocfilehash: f8334cb44042e21c086bc05c723e99b0c079fa2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677059"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="a30c5-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="a30c5-102">CorManifestResourceFlags Enumeration</span></span>

<span data-ttu-id="a30c5-103">指出組件資訊清單中已編碼之資源的可見度。</span><span class="sxs-lookup"><span data-stu-id="a30c5-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a30c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="a30c5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a30c5-105">成員</span><span class="sxs-lookup"><span data-stu-id="a30c5-105">Members</span></span>  
  
|<span data-ttu-id="a30c5-106">member</span><span class="sxs-lookup"><span data-stu-id="a30c5-106">Member</span></span>|<span data-ttu-id="a30c5-107">描述</span><span class="sxs-lookup"><span data-stu-id="a30c5-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="a30c5-108">保留的。</span><span class="sxs-lookup"><span data-stu-id="a30c5-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="a30c5-109">這些資源是公用的。</span><span class="sxs-lookup"><span data-stu-id="a30c5-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="a30c5-110">這些資源是私用的。</span><span class="sxs-lookup"><span data-stu-id="a30c5-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a30c5-111">需求</span><span class="sxs-lookup"><span data-stu-id="a30c5-111">Requirements</span></span>  

 <span data-ttu-id="a30c5-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a30c5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a30c5-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="a30c5-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a30c5-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a30c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30c5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a30c5-115">See also</span></span>

- [<span data-ttu-id="a30c5-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="a30c5-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
