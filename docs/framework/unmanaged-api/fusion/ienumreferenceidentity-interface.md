---
title: "IEnumReferenceIdentity 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="e4ce5-102">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="e4ce5-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="e4ce5-103">做為集合的列舉值`IReferenceIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="e4ce5-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4ce5-104">方法</span><span class="sxs-lookup"><span data-stu-id="e4ce5-104">Methods</span></span>  
  
|<span data-ttu-id="e4ce5-105">方法</span><span class="sxs-lookup"><span data-stu-id="e4ce5-105">Method</span></span>|<span data-ttu-id="e4ce5-106">說明</span><span class="sxs-lookup"><span data-stu-id="e4ce5-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="e4ce5-107">取得新的介面指標`IEnumReferenceIdentity`，其中包含這個相同的成員`IEnumReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e4ce5-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="e4ce5-108">取得指定的數目`IReferenceIdentity`物件，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="e4ce5-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="e4ce5-109">將指令指標移到開頭`IEnumReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e4ce5-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="e4ce5-110">將指令指標向前移以指定的項目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="e4ce5-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4ce5-111">需求</span><span class="sxs-lookup"><span data-stu-id="e4ce5-111">Requirements</span></span>  
 <span data-ttu-id="e4ce5-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4ce5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ce5-113">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e4ce5-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e4ce5-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ce5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ce5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4ce5-115">See Also</span></span>  
 [<span data-ttu-id="e4ce5-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="e4ce5-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="e4ce5-117">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="e4ce5-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
