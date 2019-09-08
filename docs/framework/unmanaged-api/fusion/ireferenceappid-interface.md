---
title: IReferenceAppId 介面
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796376"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="8168d-102">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="8168d-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="8168d-103">代表目前範圍中應用程式的唯一識別碼參考。</span><span class="sxs-lookup"><span data-stu-id="8168d-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8168d-104">方法</span><span class="sxs-lookup"><span data-stu-id="8168d-104">Methods</span></span>  
  
|<span data-ttu-id="8168d-105">方法</span><span class="sxs-lookup"><span data-stu-id="8168d-105">Method</span></span>|<span data-ttu-id="8168d-106">描述</span><span class="sxs-lookup"><span data-stu-id="8168d-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="8168d-107">取得這個`IReferenceAppId`所參考應用程式之代碼識別碼的字串表示的指標。</span><span class="sxs-lookup"><span data-stu-id="8168d-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="8168d-108">設定這個`IReferenceAppId`所參考之應用程式的代碼識別碼。</span><span class="sxs-lookup"><span data-stu-id="8168d-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="8168d-109">取得`IEnumReferenceIdentity`實例的介面指標， `IReferenceIdentity`其中包含表示這個`IReferenceAppId`之成員的實例。</span><span class="sxs-lookup"><span data-stu-id="8168d-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="8168d-110">取得這個`IReferenceAppId`之訂閱的 token 識別碼之字串表示的指標。</span><span class="sxs-lookup"><span data-stu-id="8168d-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="8168d-111">將這個`IReferenceAppId`的訂閱的 token 識別碼設定為指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="8168d-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8168d-112">需求</span><span class="sxs-lookup"><span data-stu-id="8168d-112">Requirements</span></span>  
 <span data-ttu-id="8168d-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8168d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8168d-114">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="8168d-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8168d-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8168d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8168d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8168d-116">See also</span></span>

- [<span data-ttu-id="8168d-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="8168d-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="8168d-118">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="8168d-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="8168d-119">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="8168d-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
