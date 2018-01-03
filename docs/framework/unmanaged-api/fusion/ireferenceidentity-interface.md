---
title: "IReferenceIdentity 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9696687f292d7dcaa3d430c1e269f0fedb05e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="4e840-102">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="4e840-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="4e840-103">表示唯一的簽章的程式碼物件的參考。</span><span class="sxs-lookup"><span data-stu-id="4e840-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e840-104">方法</span><span class="sxs-lookup"><span data-stu-id="4e840-104">Methods</span></span>  
  
|<span data-ttu-id="4e840-105">方法</span><span class="sxs-lookup"><span data-stu-id="4e840-105">Method</span></span>|<span data-ttu-id="4e840-106">描述</span><span class="sxs-lookup"><span data-stu-id="4e840-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="4e840-107">取得新的介面指標`IReferenceIdentity`等同於此執行個體`IReferenceIdentity`，除非有指定的屬性變更。</span><span class="sxs-lookup"><span data-stu-id="4e840-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="4e840-108">取得的介面指標`IEnumIDENTITY_ATTRIBUTE`包含與此相關聯之屬性的執行個體`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="4e840-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="4e840-109">在指定的命名空間中具有指定之名稱取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4e840-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="4e840-110">設定具有指定的命名空間與指定的名稱，以指定的值的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e840-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e840-111">需求</span><span class="sxs-lookup"><span data-stu-id="4e840-111">Requirements</span></span>  
 <span data-ttu-id="4e840-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e840-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e840-113">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="4e840-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="4e840-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e840-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e840-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e840-115">See Also</span></span>  
 [<span data-ttu-id="4e840-116">融合介面</span><span class="sxs-lookup"><span data-stu-id="4e840-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="4e840-117">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="4e840-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
