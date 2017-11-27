---
title: "IReferenceAppId 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="31953-102">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="31953-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="31953-103">代表目前範圍中的應用程式的唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="31953-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31953-104">方法</span><span class="sxs-lookup"><span data-stu-id="31953-104">Methods</span></span>  
  
|<span data-ttu-id="31953-105">方法</span><span class="sxs-lookup"><span data-stu-id="31953-105">Method</span></span>|<span data-ttu-id="31953-106">說明</span><span class="sxs-lookup"><span data-stu-id="31953-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="31953-107">取得指標所參考的應用程式的程式碼識別項的字串表示`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="31953-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="31953-108">設定所參考的應用程式的程式碼識別碼`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="31953-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="31953-109">取得的介面指標`IEnumReferenceIdentity`執行個體包含`IReferenceIdentity`代表這個成員的執行個體`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="31953-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="31953-110">取得權杖識別碼的字串表示的指標，此訂用帳戶`IReferenceAppId`。</span><span class="sxs-lookup"><span data-stu-id="31953-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="31953-111">設定此訂用帳戶的語彙基元識別碼`IReferenceAppId`設為指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="31953-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31953-112">需求</span><span class="sxs-lookup"><span data-stu-id="31953-112">Requirements</span></span>  
 <span data-ttu-id="31953-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31953-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31953-114">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="31953-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="31953-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31953-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31953-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31953-116">See Also</span></span>  
 [<span data-ttu-id="31953-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="31953-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="31953-118">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="31953-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="31953-119">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="31953-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
