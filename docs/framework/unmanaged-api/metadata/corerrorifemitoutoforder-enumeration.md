---
title: CorErrorIfEmitOutOfOrder 列舉
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007426"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="f8285-102">CorErrorIfEmitOutOfOrder 列舉</span><span class="sxs-lookup"><span data-stu-id="f8285-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="f8285-103">包含旗標值，這些值表示中繼資料未按順序發出時，在哪些條件下應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8285-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8285-104">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="f8285-105">成員</span><span class="sxs-lookup"><span data-stu-id="f8285-105">Members</span></span>  
  
|<span data-ttu-id="f8285-106">成員</span><span class="sxs-lookup"><span data-stu-id="f8285-106">Member</span></span>|<span data-ttu-id="f8285-107">描述</span><span class="sxs-lookup"><span data-stu-id="f8285-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="f8285-108">指出預設行為，這不會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="f8285-109">表示編譯器不應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="f8285-110">指出當欄位、屬性、事件、方法或參數未按順序發出時，編譯器應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="f8285-111">指出當方法未按順序發出時，編譯器應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="f8285-112">指出當欄位未按順序發出時，編譯器應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="f8285-113">指出當參數未按順序發出時，編譯器應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="f8285-114">指出當屬性未按順序發出時，編譯器應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="f8285-115">指出當事件未按順序發出時，編譯器應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8285-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8285-116">需求</span><span class="sxs-lookup"><span data-stu-id="f8285-116">Requirements</span></span>  
 <span data-ttu-id="f8285-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8285-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8285-118">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="f8285-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f8285-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8285-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8285-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8285-120">See also</span></span>

- [<span data-ttu-id="f8285-121">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f8285-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
