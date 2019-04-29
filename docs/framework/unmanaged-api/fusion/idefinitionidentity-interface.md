---
title: IDefinitionIdentity 介面
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ff23330f307c10eac134048de39a6e19a67c75b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697533"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="3e66c-102">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="3e66c-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="3e66c-103">代表目前範圍中定義應用程式的程式碼的唯一的簽章。</span><span class="sxs-lookup"><span data-stu-id="3e66c-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e66c-104">方法</span><span class="sxs-lookup"><span data-stu-id="3e66c-104">Methods</span></span>  
  
|<span data-ttu-id="3e66c-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e66c-105">Method</span></span>|<span data-ttu-id="3e66c-106">描述</span><span class="sxs-lookup"><span data-stu-id="3e66c-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="3e66c-107">取得新的介面指標`IDefinitionIdentity`物件，等於這個`IDefinitionIdentity`，但不包括指定的屬性變更。</span><span class="sxs-lookup"><span data-stu-id="3e66c-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="3e66c-108">取得的介面指標[IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)物件，其中包含與此相關聯的屬性`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="3e66c-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="3e66c-109">在指定的命名空間中取得具有指定名稱之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3e66c-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="3e66c-110">設定指定的值指定的命名空間中具有指定的名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e66c-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e66c-111">需求</span><span class="sxs-lookup"><span data-stu-id="3e66c-111">Requirements</span></span>  
 <span data-ttu-id="3e66c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e66c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e66c-113">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="3e66c-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3e66c-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e66c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e66c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e66c-115">See also</span></span>

- [<span data-ttu-id="3e66c-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="3e66c-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
