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
ms.openlocfilehash: a1a50c15071ea1e696e508c779309225c7e7bfa2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097817"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="f0dce-102">CorEventAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="f0dce-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="f0dce-103">包含值，這些值描述事件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f0dce-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0dce-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0dce-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="f0dce-105">成員</span><span class="sxs-lookup"><span data-stu-id="f0dce-105">Members</span></span>  
  
|<span data-ttu-id="f0dce-106">成員</span><span class="sxs-lookup"><span data-stu-id="f0dce-106">Member</span></span>|<span data-ttu-id="f0dce-107">描述</span><span class="sxs-lookup"><span data-stu-id="f0dce-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="f0dce-108">指定事件是特殊的且其名稱的描述方式。</span><span class="sxs-lookup"><span data-stu-id="f0dce-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="f0dce-109">保留供內部使用的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="f0dce-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="f0dce-110">指定 common language runtime 應該檢查事件名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f0dce-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0dce-111">需求</span><span class="sxs-lookup"><span data-stu-id="f0dce-111">Requirements</span></span>  
 <span data-ttu-id="f0dce-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0dce-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0dce-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f0dce-113">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="f0dce-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f0dce-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0dce-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0dce-115">See also</span></span>

- [<span data-ttu-id="f0dce-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f0dce-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
