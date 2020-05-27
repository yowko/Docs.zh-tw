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
ms.openlocfilehash: ebdff88e9fdf499b809d56c4c29a906dbef9ec40
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008972"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="67c9a-102">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="67c9a-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="67c9a-103">表示在組件資訊清單中編碼的資源可見度。</span><span class="sxs-lookup"><span data-stu-id="67c9a-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="67c9a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="67c9a-105">成員</span><span class="sxs-lookup"><span data-stu-id="67c9a-105">Members</span></span>  
  
|<span data-ttu-id="67c9a-106">成員</span><span class="sxs-lookup"><span data-stu-id="67c9a-106">Member</span></span>|<span data-ttu-id="67c9a-107">描述</span><span class="sxs-lookup"><span data-stu-id="67c9a-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="67c9a-108">已保留。</span><span class="sxs-lookup"><span data-stu-id="67c9a-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="67c9a-109">資源是公用的。</span><span class="sxs-lookup"><span data-stu-id="67c9a-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="67c9a-110">資源是私用的。</span><span class="sxs-lookup"><span data-stu-id="67c9a-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67c9a-111">需求</span><span class="sxs-lookup"><span data-stu-id="67c9a-111">Requirements</span></span>  
 <span data-ttu-id="67c9a-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67c9a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67c9a-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="67c9a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="67c9a-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67c9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c9a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67c9a-115">See also</span></span>

- [<span data-ttu-id="67c9a-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="67c9a-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
