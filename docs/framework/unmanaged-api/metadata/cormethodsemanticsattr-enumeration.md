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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f888c39160e52e550d07f58b9c5bcd11fd625658
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564077"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="60ebb-102">CorMethodSemanticsAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="60ebb-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="60ebb-103">包含值，這些值描述方法與關聯的屬性或事件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="60ebb-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ebb-104">語法</span><span class="sxs-lookup"><span data-stu-id="60ebb-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="60ebb-105">成員</span><span class="sxs-lookup"><span data-stu-id="60ebb-105">Members</span></span>  
  
|<span data-ttu-id="60ebb-106">成員</span><span class="sxs-lookup"><span data-stu-id="60ebb-106">Member</span></span>|<span data-ttu-id="60ebb-107">描述</span><span class="sxs-lookup"><span data-stu-id="60ebb-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="60ebb-108">指定的方法是`set`屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="60ebb-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="60ebb-109">指定的方法是`get`屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="60ebb-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="60ebb-110">指定方法的屬性或事件以外此處定義的關聯性。</span><span class="sxs-lookup"><span data-stu-id="60ebb-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="60ebb-111">指定此方法會加入事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="60ebb-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="60ebb-112">指定方法移除事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="60ebb-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="60ebb-113">指定該方法會引發事件。</span><span class="sxs-lookup"><span data-stu-id="60ebb-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60ebb-114">需求</span><span class="sxs-lookup"><span data-stu-id="60ebb-114">Requirements</span></span>  
 <span data-ttu-id="60ebb-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60ebb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ebb-116">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="60ebb-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="60ebb-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60ebb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ebb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60ebb-118">See also</span></span>
- [<span data-ttu-id="60ebb-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="60ebb-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
