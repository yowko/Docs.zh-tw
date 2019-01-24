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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084f0bbab130cd4e7334184fe9baa322c0487942
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616767"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="fd69b-102">CorErrorIfEmitOutOfOrder 列舉</span><span class="sxs-lookup"><span data-stu-id="fd69b-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="fd69b-103">包含旗標值，這些值表示中繼資料未按順序發出時，在哪些條件下應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd69b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd69b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="fd69b-105">成員</span><span class="sxs-lookup"><span data-stu-id="fd69b-105">Members</span></span>  
  
|<span data-ttu-id="fd69b-106">成員</span><span class="sxs-lookup"><span data-stu-id="fd69b-106">Member</span></span>|<span data-ttu-id="fd69b-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd69b-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="fd69b-108">表示預設的行為，不會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="fd69b-109">表示編譯器應該不會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="fd69b-110">表示編譯器應產生錯誤訊息，當欄位、 屬性、 事件、 方法或參數，就會發出次序不對。</span><span class="sxs-lookup"><span data-stu-id="fd69b-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="fd69b-111">指示編譯器在未按順序發出方法時，應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="fd69b-112">指示編譯器在未按順序發出欄位時，應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="fd69b-113">指示編譯器在未按順序發出參數時，應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="fd69b-114">指示編譯器在未按順序發出屬性時，應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fd69b-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="fd69b-115">表示編譯器應該產生一則錯誤訊息時就會發出事件順序。</span><span class="sxs-lookup"><span data-stu-id="fd69b-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd69b-116">需求</span><span class="sxs-lookup"><span data-stu-id="fd69b-116">Requirements</span></span>  
 <span data-ttu-id="fd69b-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd69b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd69b-118">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fd69b-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fd69b-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd69b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd69b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd69b-120">See also</span></span>
- [<span data-ttu-id="fd69b-121">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="fd69b-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
