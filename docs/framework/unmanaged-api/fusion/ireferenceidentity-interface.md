---
title: IReferenceIdentity 介面
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796352"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="fcca4-102">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="fcca4-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="fcca4-103">表示程式碼物件之唯一簽章的參考。</span><span class="sxs-lookup"><span data-stu-id="fcca4-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcca4-104">方法</span><span class="sxs-lookup"><span data-stu-id="fcca4-104">Methods</span></span>  
  
|<span data-ttu-id="fcca4-105">方法</span><span class="sxs-lookup"><span data-stu-id="fcca4-105">Method</span></span>|<span data-ttu-id="fcca4-106">說明</span><span class="sxs-lookup"><span data-stu-id="fcca4-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="fcca4-107">取得與這個`IReferenceIdentity` `IReferenceIdentity`相同的新實例介面指標，但指定的屬性變更除外。</span><span class="sxs-lookup"><span data-stu-id="fcca4-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="fcca4-108">取得`IEnumIDENTITY_ATTRIBUTE`實例的介面指標，其中包含與這個`IReferenceIdentity`相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="fcca4-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="fcca4-109">取得指定之命名空間中具有指定名稱之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="fcca4-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="fcca4-110">將具有指定之命名空間和指定名稱的屬性設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="fcca4-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcca4-111">需求</span><span class="sxs-lookup"><span data-stu-id="fcca4-111">Requirements</span></span>  
 <span data-ttu-id="fcca4-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcca4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcca4-113">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="fcca4-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="fcca4-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcca4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcca4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcca4-115">See also</span></span>

- [<span data-ttu-id="fcca4-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="fcca4-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="fcca4-117">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="fcca4-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
