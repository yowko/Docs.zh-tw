---
title: IEnumReferenceIdentity 介面
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697247"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="cbad8-102">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="cbad8-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="cbad8-103">做為集合的列舉程式`IReferenceIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="cbad8-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbad8-104">方法</span><span class="sxs-lookup"><span data-stu-id="cbad8-104">Methods</span></span>  
  
|<span data-ttu-id="cbad8-105">方法</span><span class="sxs-lookup"><span data-stu-id="cbad8-105">Method</span></span>|<span data-ttu-id="cbad8-106">描述</span><span class="sxs-lookup"><span data-stu-id="cbad8-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="cbad8-107">取得新的介面指標`IEnumReferenceIdentity`，其中包含與這個相同的成員`IEnumReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="cbad8-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="cbad8-108">取得指定的數目`IReferenceIdentity`物件，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="cbad8-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="cbad8-109">將指令指標移至這個開頭`IEnumReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="cbad8-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="cbad8-110">將指令指標向前移的指定項目數，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="cbad8-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbad8-111">需求</span><span class="sxs-lookup"><span data-stu-id="cbad8-111">Requirements</span></span>  
 <span data-ttu-id="cbad8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cbad8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbad8-113">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="cbad8-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="cbad8-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbad8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbad8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbad8-115">See also</span></span>

- [<span data-ttu-id="cbad8-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="cbad8-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="cbad8-117">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="cbad8-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
