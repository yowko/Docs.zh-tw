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
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673861"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="f8d02-102">IDefinitionAppId 介面</span><span class="sxs-lookup"><span data-stu-id="f8d02-102">IDefinitionAppId Interface</span></span>

<span data-ttu-id="f8d02-103">表示在目前範圍中定義應用程式之程式碼的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="f8d02-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8d02-104">方法</span><span class="sxs-lookup"><span data-stu-id="f8d02-104">Methods</span></span>  
  
|<span data-ttu-id="f8d02-105">方法</span><span class="sxs-lookup"><span data-stu-id="f8d02-105">Method</span></span>|<span data-ttu-id="f8d02-106">描述</span><span class="sxs-lookup"><span data-stu-id="f8d02-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="f8d02-107">取得表示此物件中之程式碼的格式化字串 `IDefinitionAppId` 。</span><span class="sxs-lookup"><span data-stu-id="f8d02-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="f8d02-108">將這個物件的程式碼設定 `IDefinitionAppId` 為指定的格式化字串值。</span><span class="sxs-lookup"><span data-stu-id="f8d02-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="f8d02-109">取得 [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) 物件的介面指標，該物件包含目前應用程式路徑中的元件。</span><span class="sxs-lookup"><span data-stu-id="f8d02-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="f8d02-110">將目前範圍中元件的應用程式路徑設定為指定之 [IDefinitionIdentity](idefinitionidentity-interface.md) 物件所參考的值。</span><span class="sxs-lookup"><span data-stu-id="f8d02-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="f8d02-111">取得這個物件之訂閱的標記識別項之字串表示的指標 `IDefinitionAppId` 。</span><span class="sxs-lookup"><span data-stu-id="f8d02-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="f8d02-112">將這個物件之訂閱的標記識別項設定 `IDefinitionAppId` 為指定的字串值。</span><span class="sxs-lookup"><span data-stu-id="f8d02-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8d02-113">需求</span><span class="sxs-lookup"><span data-stu-id="f8d02-113">Requirements</span></span>  

 <span data-ttu-id="f8d02-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8d02-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d02-115">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="f8d02-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f8d02-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d02-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d02-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d02-117">See also</span></span>

- [<span data-ttu-id="f8d02-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="f8d02-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
