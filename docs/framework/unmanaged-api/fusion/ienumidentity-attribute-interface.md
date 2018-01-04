---
title: "IEnumIDENTITY_ATTRIBUTE 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc77f2106f5063b8db25f375c354a15f9f936e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="6bca3-102">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="6bca3-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="6bca3-103">可做為目前範圍中的程式碼物件的屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="6bca3-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bca3-104">方法</span><span class="sxs-lookup"><span data-stu-id="6bca3-104">Methods</span></span>  
  
|<span data-ttu-id="6bca3-105">方法</span><span class="sxs-lookup"><span data-stu-id="6bca3-105">Method</span></span>|<span data-ttu-id="6bca3-106">描述</span><span class="sxs-lookup"><span data-stu-id="6bca3-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="6bca3-107">取得新的介面指標`IEnumIDENTITY_ATTRIBUTE`，其中包含這個相同的成員`IEnumIDENTITY_ATTRIBUTE`。</span><span class="sxs-lookup"><span data-stu-id="6bca3-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="6bca3-108">將這個項目中所包含的資料寫入`IEnumIDENTITY_ATTRIBUTE`指定的資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6bca3-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="6bca3-109">取得指定的數目的屬性，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="6bca3-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="6bca3-110">將指令指標移到開頭`IEnumIDENTITY_ATTRIBUTE`。</span><span class="sxs-lookup"><span data-stu-id="6bca3-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="6bca3-111">將指令指標向前移以指定的項目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="6bca3-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bca3-112">需求</span><span class="sxs-lookup"><span data-stu-id="6bca3-112">Requirements</span></span>  
 <span data-ttu-id="6bca3-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bca3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bca3-114">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="6bca3-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="6bca3-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bca3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bca3-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6bca3-116">See Also</span></span>  
 [<span data-ttu-id="6bca3-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="6bca3-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
