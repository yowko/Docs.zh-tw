---
title: "CorNotificationForTokenMovement 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e1d3ad11867dbd06dfe3f43cc31817a44cb96d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="10634-102">CorNotificationForTokenMovement 列舉</span><span class="sxs-lookup"><span data-stu-id="10634-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="10634-103">指定權杖的重新對應時將中繼資料 API 用戶端傳送的通知。</span><span class="sxs-lookup"><span data-stu-id="10634-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10634-104">語法</span><span class="sxs-lookup"><span data-stu-id="10634-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="10634-105">成員</span><span class="sxs-lookup"><span data-stu-id="10634-105">Members</span></span>  
  
|<span data-ttu-id="10634-106">成員</span><span class="sxs-lookup"><span data-stu-id="10634-106">Member</span></span>|<span data-ttu-id="10634-107">描述</span><span class="sxs-lookup"><span data-stu-id="10634-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="10634-108">通知`mdTypeRef`， `mdMethodDef`， `mdMemberRef`，或`mdFieldDef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="10634-109">語彙基元移動時，通知。</span><span class="sxs-lookup"><span data-stu-id="10634-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="10634-110">不通知語彙基元移動時。</span><span class="sxs-lookup"><span data-stu-id="10634-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="10634-111">通知`mdMethodDef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="10634-112">通知`mdMemberRef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="10634-113">通知`mdFieldDef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="10634-114">通知`mdTypeRef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="10634-115">通知`mdTypeDef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="10634-116">通知`mdParamDef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="10634-117">通知`mdInterfaceImpl`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="10634-118">通知`mdProperty`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="10634-119">通知`mdEvent`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="10634-120">通知`mdSignature`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="10634-121">通知`mdTypeSpec`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="10634-122">通知`mdCustomAttribute`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="10634-123">通知`mdSecurityValue`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="10634-124">通知`mdPermission`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="10634-125">通知`mdModuleRef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="10634-126">通知`mdNameSpace`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="10634-127">通知`mdAssemblyRef`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="10634-128">通知`mdFile`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="10634-129">通知`mdExportedType`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="10634-130">通知`mdManifestResource`語彙基元移動。</span><span class="sxs-lookup"><span data-stu-id="10634-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10634-131">備註</span><span class="sxs-lookup"><span data-stu-id="10634-131">Remarks</span></span>  
 <span data-ttu-id="10634-132">語彙基元可能會重新對應 （也就是指移動） 期間的中繼資料合併。</span><span class="sxs-lookup"><span data-stu-id="10634-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10634-133">需求</span><span class="sxs-lookup"><span data-stu-id="10634-133">Requirements</span></span>  
 <span data-ttu-id="10634-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10634-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10634-135">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="10634-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="10634-136">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10634-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10634-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="10634-137">See Also</span></span>  
 [<span data-ttu-id="10634-138">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="10634-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
