---
title: IDefinitionAppId 介面
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697234"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="26a49-102">IDefinitionAppId 介面</span><span class="sxs-lookup"><span data-stu-id="26a49-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="26a49-103">代表目前範圍中定義應用程式的程式碼的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="26a49-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26a49-104">方法</span><span class="sxs-lookup"><span data-stu-id="26a49-104">Methods</span></span>  
  
|<span data-ttu-id="26a49-105">方法</span><span class="sxs-lookup"><span data-stu-id="26a49-105">Method</span></span>|<span data-ttu-id="26a49-106">描述</span><span class="sxs-lookup"><span data-stu-id="26a49-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="26a49-107">取得格式化的字串，表示在此程式碼`IDefinitionAppId`物件。</span><span class="sxs-lookup"><span data-stu-id="26a49-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="26a49-108">設定這個程式碼`IDefinitionAppId`至指定的物件格式化的字串值。</span><span class="sxs-lookup"><span data-stu-id="26a49-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="26a49-109">取得的介面指標[IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)物件，包含目前的應用程式路徑中的組件。</span><span class="sxs-lookup"><span data-stu-id="26a49-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="26a49-110">設定組件參考所指定的值是目前範圍中的應用程式路徑[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="26a49-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="26a49-111">此訂用帳戶取得的 token 識別碼的字串表示的指標`IDefinitionAppId`物件。</span><span class="sxs-lookup"><span data-stu-id="26a49-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="26a49-112">此設定訂用帳戶的語彙基元識別碼`IDefinitionAppId`物件到指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="26a49-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26a49-113">需求</span><span class="sxs-lookup"><span data-stu-id="26a49-113">Requirements</span></span>  
 <span data-ttu-id="26a49-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26a49-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26a49-115">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="26a49-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="26a49-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26a49-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a49-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a49-117">See also</span></span>

- [<span data-ttu-id="26a49-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="26a49-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
