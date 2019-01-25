---
title: CorEventAttr 列舉
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34aa954126cc26519aaea963f99299e5557d2c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743047"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="56883-102">CorEventAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="56883-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="56883-103">包含值，這些值描述事件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="56883-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56883-104">語法</span><span class="sxs-lookup"><span data-stu-id="56883-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="56883-105">成員</span><span class="sxs-lookup"><span data-stu-id="56883-105">Members</span></span>  
  
|<span data-ttu-id="56883-106">成員</span><span class="sxs-lookup"><span data-stu-id="56883-106">Member</span></span>|<span data-ttu-id="56883-107">描述</span><span class="sxs-lookup"><span data-stu-id="56883-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="56883-108">指定事件是特殊的且其名稱的描述方式。</span><span class="sxs-lookup"><span data-stu-id="56883-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="56883-109">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="56883-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="56883-110">指定 common language runtime 應該檢查事件名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="56883-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56883-111">需求</span><span class="sxs-lookup"><span data-stu-id="56883-111">Requirements</span></span>  
 <span data-ttu-id="56883-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56883-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56883-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="56883-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="56883-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56883-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56883-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56883-115">See also</span></span>
- [<span data-ttu-id="56883-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="56883-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
