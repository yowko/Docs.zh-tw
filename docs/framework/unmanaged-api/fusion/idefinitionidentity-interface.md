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
ms.openlocfilehash: 4f08fbbf9c8be16dff092327713e731c5aa14661
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732862"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="10919-102">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="10919-102">IDefinitionIdentity Interface</span></span>

<span data-ttu-id="10919-103">表示在目前範圍中定義應用程式之程式碼的唯一簽章。</span><span class="sxs-lookup"><span data-stu-id="10919-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10919-104">方法</span><span class="sxs-lookup"><span data-stu-id="10919-104">Methods</span></span>  
  
|<span data-ttu-id="10919-105">方法</span><span class="sxs-lookup"><span data-stu-id="10919-105">Method</span></span>|<span data-ttu-id="10919-106">描述</span><span class="sxs-lookup"><span data-stu-id="10919-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="10919-107">取得與 `IDefinitionIdentity` 此相同之新物件的介面指標 `IDefinitionIdentity` ，但指定的屬性變更除外。</span><span class="sxs-lookup"><span data-stu-id="10919-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="10919-108">取得 [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) 物件的介面指標，其中包含與這個相關聯的屬性 `IDefinitionIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="10919-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="10919-109">取得指定的命名空間中具有指定名稱之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="10919-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="10919-110">將指定的命名空間中具有指定之名稱的屬性設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="10919-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10919-111">需求</span><span class="sxs-lookup"><span data-stu-id="10919-111">Requirements</span></span>  

 <span data-ttu-id="10919-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10919-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10919-113">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="10919-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="10919-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10919-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10919-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10919-115">See also</span></span>

- [<span data-ttu-id="10919-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="10919-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
