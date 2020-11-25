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
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728611"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="351e1-102">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="351e1-102">IReferenceAppId Interface</span></span>

<span data-ttu-id="351e1-103">代表目前範圍中應用程式之唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="351e1-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="351e1-104">方法</span><span class="sxs-lookup"><span data-stu-id="351e1-104">Methods</span></span>  
  
|<span data-ttu-id="351e1-105">方法</span><span class="sxs-lookup"><span data-stu-id="351e1-105">Method</span></span>|<span data-ttu-id="351e1-106">描述</span><span class="sxs-lookup"><span data-stu-id="351e1-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="351e1-107">取得這個所參考之應用程式之程式碼識別碼的字串標記法指標 `IReferenceAppId` 。</span><span class="sxs-lookup"><span data-stu-id="351e1-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="351e1-108">設定這個所參考之應用程式的程式碼識別碼 `IReferenceAppId` 。</span><span class="sxs-lookup"><span data-stu-id="351e1-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="351e1-109">取得實例的介面指標， `IEnumReferenceIdentity` 其中包含 `IReferenceIdentity` 代表這個之成員的實例 `IReferenceAppId` 。</span><span class="sxs-lookup"><span data-stu-id="351e1-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="351e1-110">取得這個的訂閱之標記識別項的字串表示指標 `IReferenceAppId` 。</span><span class="sxs-lookup"><span data-stu-id="351e1-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="351e1-111">將訂閱的標記識別項設定為 `IReferenceAppId` 指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="351e1-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="351e1-112">需求</span><span class="sxs-lookup"><span data-stu-id="351e1-112">Requirements</span></span>  

 <span data-ttu-id="351e1-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="351e1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="351e1-114">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="351e1-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="351e1-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="351e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="351e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="351e1-116">See also</span></span>

- [<span data-ttu-id="351e1-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="351e1-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="351e1-118">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="351e1-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="351e1-119">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="351e1-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
