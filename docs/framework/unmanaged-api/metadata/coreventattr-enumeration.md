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
ms.openlocfilehash: e22b390271a7813dd1d34aecf5f8a62d7eb81005
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007430"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="b67b7-102">CorEventAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="b67b7-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="b67b7-103">包含值，這些值描述事件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b67b7-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b67b7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b67b7-105">成員</span><span class="sxs-lookup"><span data-stu-id="b67b7-105">Members</span></span>  
  
|<span data-ttu-id="b67b7-106">成員</span><span class="sxs-lookup"><span data-stu-id="b67b7-106">Member</span></span>|<span data-ttu-id="b67b7-107">描述</span><span class="sxs-lookup"><span data-stu-id="b67b7-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="b67b7-108">指定事件是特殊的，而且其名稱描述了做法。</span><span class="sxs-lookup"><span data-stu-id="b67b7-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="b67b7-109">保留供 common language runtime 內部使用。</span><span class="sxs-lookup"><span data-stu-id="b67b7-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="b67b7-110">指定通用語言執行時間應該檢查事件名稱的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b67b7-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b67b7-111">需求</span><span class="sxs-lookup"><span data-stu-id="b67b7-111">Requirements</span></span>  
 <span data-ttu-id="b67b7-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b67b7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b67b7-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="b67b7-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b67b7-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b67b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67b7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b67b7-115">See also</span></span>

- [<span data-ttu-id="b67b7-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="b67b7-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
