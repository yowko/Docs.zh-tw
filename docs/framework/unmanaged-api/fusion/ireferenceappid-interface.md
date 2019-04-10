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
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157192"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="da7e7-102">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="da7e7-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="da7e7-103">代表目前範圍中的應用程式的唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="da7e7-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da7e7-104">方法</span><span class="sxs-lookup"><span data-stu-id="da7e7-104">Methods</span></span>  
  
|<span data-ttu-id="da7e7-105">方法</span><span class="sxs-lookup"><span data-stu-id="da7e7-105">Method</span></span>|<span data-ttu-id="da7e7-106">描述</span><span class="sxs-lookup"><span data-stu-id="da7e7-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="da7e7-107">取得指標所參考的應用程式的程式碼識別項的字串表示`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="da7e7-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="da7e7-108">設定應用程式所參考的程式碼識別碼`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="da7e7-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="da7e7-109">取得的介面指標`IEnumReferenceIdentity`執行個體，包含`IReferenceIdentity`執行個體，表示這個成員`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="da7e7-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="da7e7-110">此訂用帳戶取得的 token 識別碼的字串表示的指標`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="da7e7-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="da7e7-111">此設定訂用帳戶的語彙基元識別碼`IReferenceAppId`設為指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="da7e7-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da7e7-112">需求</span><span class="sxs-lookup"><span data-stu-id="da7e7-112">Requirements</span></span>  
 <span data-ttu-id="da7e7-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da7e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7e7-114">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="da7e7-114">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="da7e7-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="da7e7-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da7e7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da7e7-116">See also</span></span>

- [<span data-ttu-id="da7e7-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="da7e7-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="da7e7-118">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="da7e7-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="da7e7-119">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="da7e7-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
