---
title: IEnumIDENTITY_ATTRIBUTE 介面
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ae940946c56cbc858690cccce61597d0016e40c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571804"
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="9aa21-102">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="9aa21-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="9aa21-103">可做為目前範圍中的程式碼物件的屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9aa21-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9aa21-104">方法</span><span class="sxs-lookup"><span data-stu-id="9aa21-104">Methods</span></span>  
  
|<span data-ttu-id="9aa21-105">方法</span><span class="sxs-lookup"><span data-stu-id="9aa21-105">Method</span></span>|<span data-ttu-id="9aa21-106">描述</span><span class="sxs-lookup"><span data-stu-id="9aa21-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="9aa21-107">取得新的介面指標`IEnumIDENTITY_ATTRIBUTE`，其中包含與這個相同的成員`IEnumIDENTITY_ATTRIBUTE`。</span><span class="sxs-lookup"><span data-stu-id="9aa21-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="9aa21-108">這個項目中所包含的資料寫入`IEnumIDENTITY_ATTRIBUTE`指定的資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9aa21-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="9aa21-109">取得指定的屬性數目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="9aa21-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="9aa21-110">將指令指標移至這個開頭`IEnumIDENTITY_ATTRIBUTE`。</span><span class="sxs-lookup"><span data-stu-id="9aa21-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="9aa21-111">將指令指標向前移的指定項目數，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="9aa21-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9aa21-112">需求</span><span class="sxs-lookup"><span data-stu-id="9aa21-112">Requirements</span></span>  
 <span data-ttu-id="9aa21-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa21-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa21-114">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9aa21-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9aa21-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa21-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa21-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9aa21-116">See also</span></span>
- [<span data-ttu-id="9aa21-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="9aa21-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
