---
title: "IReferenceAppId 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="a3231-102">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="a3231-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="a3231-103">代表目前範圍中的應用程式的唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="a3231-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3231-104">方法</span><span class="sxs-lookup"><span data-stu-id="a3231-104">Methods</span></span>  
  
|<span data-ttu-id="a3231-105">方法</span><span class="sxs-lookup"><span data-stu-id="a3231-105">Method</span></span>|<span data-ttu-id="a3231-106">描述</span><span class="sxs-lookup"><span data-stu-id="a3231-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="a3231-107">取得指標所參考的應用程式的程式碼識別項的字串表示`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="a3231-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="a3231-108">設定所參考的應用程式的程式碼識別碼`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="a3231-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="a3231-109">取得的介面指標`IEnumReferenceIdentity`執行個體包含`IReferenceIdentity`代表這個成員的執行個體`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="a3231-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="a3231-110">取得權杖識別碼的字串表示的指標，此訂用帳戶`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="a3231-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="a3231-111">設定此訂用帳戶的語彙基元識別碼`IReferenceAppId`設為指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="a3231-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3231-112">需求</span><span class="sxs-lookup"><span data-stu-id="a3231-112">Requirements</span></span>  
 <span data-ttu-id="a3231-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3231-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3231-114">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a3231-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a3231-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3231-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3231-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a3231-116">See Also</span></span>  
 [<span data-ttu-id="a3231-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="a3231-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="a3231-118">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="a3231-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="a3231-119">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="a3231-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
