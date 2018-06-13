---
title: IIdentityAuthority 介面
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 692ac4ef4fe8ea64c6a63dc2f02cc04244a842c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432519"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="e5ca0-102">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="e5ca0-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="e5ca0-103">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5ca0-104">方法</span><span class="sxs-lookup"><span data-stu-id="e5ca0-104">Methods</span></span>  
  
|<span data-ttu-id="e5ca0-105">方法</span><span class="sxs-lookup"><span data-stu-id="e5ca0-105">Method</span></span>|<span data-ttu-id="e5ca0-106">描述</span><span class="sxs-lookup"><span data-stu-id="e5ca0-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="e5ca0-107">取得值，指出兩個指定[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體會相等。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="e5ca0-108">取得值，指出兩個指定[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)執行個體會相等。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="e5ca0-109">取得值，指出兩個指定的字串定義識別的表示是否相等。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="e5ca0-110">取得值，指出兩個指定的字串參考識別表示法是否相等。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="e5ca0-111">取得新的指標`IDefinitionIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="e5ca0-112">取得新的指標`IReferenceIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="e5ca0-113">取得指定的格式化的字串版`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="e5ca0-114">填滿指定的字串版本指定寬字元緩衝區`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="e5ca0-115">取得值，指出是否指定`IDefinitionIdentity`和`IReferenceIdentity`執行個體會參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="e5ca0-116">取得值，指出指定的字串是否參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="e5ca0-117">取得的指標，新建的字串索引鍵指定`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="e5ca0-118">取得的指標，新建的字串索引鍵指定`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="e5ca0-119">取得指定雜湊值`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="e5ca0-120">取得指定雜湊值`IreferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="e5ca0-121">取得指定的格式化的字串版`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="e5ca0-122">填滿指定的字串版本指定寬字元緩衝區`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="e5ca0-123">取得的介面指標`IDefinitionIdentity`產生從指定的執行個體的格式字串。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="e5ca0-124">取得的介面指標`IReferenceIdentity`產生從指定的執行個體的格式字串。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5ca0-125">需求</span><span class="sxs-lookup"><span data-stu-id="e5ca0-125">Requirements</span></span>  
 <span data-ttu-id="e5ca0-126">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5ca0-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ca0-127">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e5ca0-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e5ca0-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ca0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ca0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5ca0-129">See Also</span></span>  
 [<span data-ttu-id="e5ca0-130">融合介面</span><span class="sxs-lookup"><span data-stu-id="e5ca0-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
