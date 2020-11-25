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
ms.openlocfilehash: 71a6ea9f593da093985a4420e690f1bdd7f9d139
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728988"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="e3152-102">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="e3152-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>

<span data-ttu-id="e3152-103">作為目前範圍中程式碼物件之屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e3152-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3152-104">方法</span><span class="sxs-lookup"><span data-stu-id="e3152-104">Methods</span></span>  
  
|<span data-ttu-id="e3152-105">方法</span><span class="sxs-lookup"><span data-stu-id="e3152-105">Method</span></span>|<span data-ttu-id="e3152-106">描述</span><span class="sxs-lookup"><span data-stu-id="e3152-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="e3152-107">取得新的介面指標， `IEnumIDENTITY_ATTRIBUTE` 其中包含與這個相同的成員 `IEnumIDENTITY_ATTRIBUTE` 。</span><span class="sxs-lookup"><span data-stu-id="e3152-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="e3152-108">將此專案中包含的資料寫入 `IEnumIDENTITY_ATTRIBUTE` 至指定的資料緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e3152-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="e3152-109">從目前位置開始取得指定數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3152-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="e3152-110">將指令指標移至這個的開頭 `IEnumIDENTITY_ATTRIBUTE` 。</span><span class="sxs-lookup"><span data-stu-id="e3152-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="e3152-111">從目前位置開始，將指令指標向下移動指定數目的元素。</span><span class="sxs-lookup"><span data-stu-id="e3152-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3152-112">需求</span><span class="sxs-lookup"><span data-stu-id="e3152-112">Requirements</span></span>  

 <span data-ttu-id="e3152-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3152-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3152-114">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="e3152-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e3152-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3152-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3152-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3152-116">See also</span></span>

- [<span data-ttu-id="e3152-117">融合介面</span><span class="sxs-lookup"><span data-stu-id="e3152-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
