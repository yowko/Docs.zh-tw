---
title: CorMethodSemanticsAttr 列舉
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: bab215a8221696a0e43e228278085fcef52a40e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442819"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="bb53f-102">CorMethodSemanticsAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="bb53f-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="bb53f-103">包含值，這些值描述方法與關聯的屬性或事件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="bb53f-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb53f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb53f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="bb53f-105">Members</span><span class="sxs-lookup"><span data-stu-id="bb53f-105">Members</span></span>  
  
|<span data-ttu-id="bb53f-106">成員</span><span class="sxs-lookup"><span data-stu-id="bb53f-106">Member</span></span>|<span data-ttu-id="bb53f-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb53f-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="bb53f-108">指定方法是屬性的 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="bb53f-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="bb53f-109">指定方法是屬性的 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="bb53f-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="bb53f-110">指定方法與屬性或事件（而非此處定義的）具有關聯性。</span><span class="sxs-lookup"><span data-stu-id="bb53f-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="bb53f-111">指定方法加入事件的處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="bb53f-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="bb53f-112">指定方法會移除事件的處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="bb53f-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="bb53f-113">指定方法會引發事件。</span><span class="sxs-lookup"><span data-stu-id="bb53f-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb53f-114">需求</span><span class="sxs-lookup"><span data-stu-id="bb53f-114">Requirements</span></span>  
 <span data-ttu-id="bb53f-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb53f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb53f-116">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="bb53f-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bb53f-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb53f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb53f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb53f-118">See also</span></span>

- [<span data-ttu-id="bb53f-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="bb53f-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
