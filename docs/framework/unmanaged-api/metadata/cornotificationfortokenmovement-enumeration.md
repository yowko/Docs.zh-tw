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
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450154"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="0c8f4-102">CorNotificationForTokenMovement 列舉</span><span class="sxs-lookup"><span data-stu-id="0c8f4-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="0c8f4-103">指定當權杖重新對應發生時，將傳送至中繼資料 API 用戶端的通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c8f4-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="0c8f4-105">Members</span><span class="sxs-lookup"><span data-stu-id="0c8f4-105">Members</span></span>  
  
|<span data-ttu-id="0c8f4-106">成員</span><span class="sxs-lookup"><span data-stu-id="0c8f4-106">Member</span></span>|<span data-ttu-id="0c8f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="0c8f4-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="0c8f4-108">在 `mdTypeRef`、`mdMethodDef`、`mdMemberRef`或 `mdFieldDef` 的權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="0c8f4-109">在任何權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="0c8f4-110">當令牌移動時不要通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="0c8f4-111">在 `mdMethodDef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="0c8f4-112">在 `mdMemberRef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="0c8f4-113">在 `mdFieldDef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="0c8f4-114">在 `mdTypeRef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="0c8f4-115">在 `mdTypeDef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="0c8f4-116">在 `mdParamDef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="0c8f4-117">在 `mdInterfaceImpl` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="0c8f4-118">在 `mdProperty` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="0c8f4-119">在 `mdEvent` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="0c8f4-120">在 `mdSignature` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="0c8f4-121">在 `mdTypeSpec` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="0c8f4-122">在 `mdCustomAttribute` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="0c8f4-123">在 `mdSecurityValue` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="0c8f4-124">在 `mdPermission` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="0c8f4-125">在 `mdModuleRef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="0c8f4-126">在 `mdNameSpace` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="0c8f4-127">在 `mdAssemblyRef` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="0c8f4-128">在 `mdFile` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="0c8f4-129">在 `mdExportedType` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="0c8f4-130">在 `mdManifestResource` 權杖移動時通知。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8f4-131">備註</span><span class="sxs-lookup"><span data-stu-id="0c8f4-131">Remarks</span></span>  
 <span data-ttu-id="0c8f4-132">在中繼資料合併期間，權杖可能會重新對應（也就是移動）。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8f4-133">需求</span><span class="sxs-lookup"><span data-stu-id="0c8f4-133">Requirements</span></span>  
 <span data-ttu-id="0c8f4-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c8f4-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8f4-135">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="0c8f4-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0c8f4-136">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8f4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8f4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c8f4-137">See also</span></span>

- [<span data-ttu-id="0c8f4-138">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="0c8f4-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
