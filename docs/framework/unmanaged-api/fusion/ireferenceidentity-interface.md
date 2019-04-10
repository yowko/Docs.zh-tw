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
ms.openlocfilehash: dd46ea26532074c9ea42da4d07a38ed583aad076
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220158"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="4d67f-102">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="4d67f-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="4d67f-103">表示唯一的簽章的程式碼物件的參考。</span><span class="sxs-lookup"><span data-stu-id="4d67f-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d67f-104">方法</span><span class="sxs-lookup"><span data-stu-id="4d67f-104">Methods</span></span>  
  
|<span data-ttu-id="4d67f-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d67f-105">Method</span></span>|<span data-ttu-id="4d67f-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d67f-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="4d67f-107">取得新的介面指標`IReferenceIdentity`等於這個執行個體`IReferenceIdentity`，但不包括指定的屬性變更。</span><span class="sxs-lookup"><span data-stu-id="4d67f-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="4d67f-108">取得的介面指標`IEnumIDENTITY_ATTRIBUTE`執行個體，包含與此相關聯的屬性`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="4d67f-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="4d67f-109">取得屬性的值中指定的命名空間，以指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d67f-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="4d67f-110">設定具有指定的命名空間和指定的值指定之名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="4d67f-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d67f-111">需求</span><span class="sxs-lookup"><span data-stu-id="4d67f-111">Requirements</span></span>  
 <span data-ttu-id="4d67f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d67f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d67f-113">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="4d67f-113">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="4d67f-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4d67f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d67f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d67f-115">See also</span></span>

- [<span data-ttu-id="4d67f-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="4d67f-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="4d67f-117">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="4d67f-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
