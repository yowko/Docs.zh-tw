---
title: CorNotificationForTokenMovement 列舉
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15c5e8b34f2748868611bd7dc47ef73c491b1338
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189426"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="89130-102">CorNotificationForTokenMovement 列舉</span><span class="sxs-lookup"><span data-stu-id="89130-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="89130-103">指定權杖的重新對應發生時將中繼資料 API 用戶端傳送的通知。</span><span class="sxs-lookup"><span data-stu-id="89130-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89130-104">語法</span><span class="sxs-lookup"><span data-stu-id="89130-104">Syntax</span></span>  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="89130-105">成員</span><span class="sxs-lookup"><span data-stu-id="89130-105">Members</span></span>  
  
|<span data-ttu-id="89130-106">成員</span><span class="sxs-lookup"><span data-stu-id="89130-106">Member</span></span>|<span data-ttu-id="89130-107">描述</span><span class="sxs-lookup"><span data-stu-id="89130-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="89130-108">時通知我`mdTypeRef`， `mdMethodDef`， `mdMemberRef`，或`mdFieldDef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="89130-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="89130-109">語彙基元移動時，就會通知。</span><span class="sxs-lookup"><span data-stu-id="89130-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="89130-110">不通知語彙基元移動時。</span><span class="sxs-lookup"><span data-stu-id="89130-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="89130-111">通知時機`mdMethodDef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="89130-112">通知時機`mdMemberRef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="89130-113">通知時機`mdFieldDef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="89130-114">通知時機`mdTypeRef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="89130-115">通知時機`mdTypeDef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="89130-116">通知時機`mdParamDef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="89130-117">通知時機`mdInterfaceImpl`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="89130-118">通知時機`mdProperty`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="89130-119">通知時機`mdEvent`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="89130-120">通知時機`mdSignature`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="89130-121">通知時機`mdTypeSpec`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="89130-122">通知時機`mdCustomAttribute`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="89130-123">通知時機`mdSecurityValue`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="89130-124">通知時機`mdPermission`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="89130-125">通知時機`mdModuleRef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="89130-126">通知時機`mdNameSpace`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="89130-127">通知時機`mdAssemblyRef`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="89130-128">通知時機`mdFile`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="89130-129">通知時機`mdExportedType`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="89130-130">通知時機`mdManifestResource`k 的移動。</span><span class="sxs-lookup"><span data-stu-id="89130-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89130-131">備註</span><span class="sxs-lookup"><span data-stu-id="89130-131">Remarks</span></span>  
 <span data-ttu-id="89130-132">語彙基元可能會重新對應 （也就是指移動） 期間的中繼資料合併。</span><span class="sxs-lookup"><span data-stu-id="89130-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89130-133">需求</span><span class="sxs-lookup"><span data-stu-id="89130-133">Requirements</span></span>  
 <span data-ttu-id="89130-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89130-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89130-135">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="89130-135">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="89130-136">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="89130-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="89130-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89130-137">See also</span></span>

- [<span data-ttu-id="89130-138">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="89130-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
