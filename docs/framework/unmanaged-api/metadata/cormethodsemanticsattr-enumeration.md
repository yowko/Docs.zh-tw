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
ms.openlocfilehash: de467c98dfa7ad3eac69502f2afe311b301e1ec5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444805"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="85549-102">CorMethodSemanticsAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="85549-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="85549-103">包含值，這些值描述方法與關聯的屬性或事件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="85549-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85549-104">語法</span><span class="sxs-lookup"><span data-stu-id="85549-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="85549-105">成員</span><span class="sxs-lookup"><span data-stu-id="85549-105">Members</span></span>  
  
|<span data-ttu-id="85549-106">成員</span><span class="sxs-lookup"><span data-stu-id="85549-106">Member</span></span>|<span data-ttu-id="85549-107">描述</span><span class="sxs-lookup"><span data-stu-id="85549-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="85549-108">指定的方法是`set`屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="85549-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="85549-109">指定的方法是`get`屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="85549-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="85549-110">指定的方法有屬性或事件以外此處定義的關聯性。</span><span class="sxs-lookup"><span data-stu-id="85549-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="85549-111">指定此方法會加入事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="85549-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="85549-112">指定方法中移除事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="85549-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="85549-113">指定此方法會引發事件。</span><span class="sxs-lookup"><span data-stu-id="85549-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85549-114">需求</span><span class="sxs-lookup"><span data-stu-id="85549-114">Requirements</span></span>  
 <span data-ttu-id="85549-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85549-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85549-116">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="85549-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="85549-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85549-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85549-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85549-118">See Also</span></span>  
 [<span data-ttu-id="85549-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="85549-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
