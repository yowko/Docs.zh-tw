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
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796461"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="79fbe-102">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="79fbe-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="79fbe-103">作為目前範圍中程式碼物件屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="79fbe-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79fbe-104">方法</span><span class="sxs-lookup"><span data-stu-id="79fbe-104">Methods</span></span>  
  
|<span data-ttu-id="79fbe-105">方法</span><span class="sxs-lookup"><span data-stu-id="79fbe-105">Method</span></span>|<span data-ttu-id="79fbe-106">描述</span><span class="sxs-lookup"><span data-stu-id="79fbe-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="79fbe-107">取得新`IEnumIDENTITY_ATTRIBUTE`的介面指標，其中包含與這個`IEnumIDENTITY_ATTRIBUTE`相同的成員。</span><span class="sxs-lookup"><span data-stu-id="79fbe-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="79fbe-108">將此`IEnumIDENTITY_ATTRIBUTE`專案中包含的資料寫入指定的資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="79fbe-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="79fbe-109">取得指定數目的屬性，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="79fbe-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="79fbe-110">將指令指標移至這個`IEnumIDENTITY_ATTRIBUTE`的開頭。</span><span class="sxs-lookup"><span data-stu-id="79fbe-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="79fbe-111">從目前位置開始，將指令指標向下移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="79fbe-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79fbe-112">需求</span><span class="sxs-lookup"><span data-stu-id="79fbe-112">Requirements</span></span>  
 <span data-ttu-id="79fbe-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79fbe-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79fbe-114">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="79fbe-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="79fbe-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79fbe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fbe-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79fbe-116">See also</span></span>

- [<span data-ttu-id="79fbe-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="79fbe-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
