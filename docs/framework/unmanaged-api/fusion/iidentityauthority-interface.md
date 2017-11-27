---
title: "IIdentityAuthority 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IIdentityAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IIdentityAuthority
helpviewer_keywords: IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3f38d932fa0376186e2c22232d21857d5fa128f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="84705-102">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="84705-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="84705-103">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="84705-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84705-104">方法</span><span class="sxs-lookup"><span data-stu-id="84705-104">Methods</span></span>  
  
|<span data-ttu-id="84705-105">方法</span><span class="sxs-lookup"><span data-stu-id="84705-105">Method</span></span>|<span data-ttu-id="84705-106">說明</span><span class="sxs-lookup"><span data-stu-id="84705-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="84705-107">取得值，指出兩個指定[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體會相等。</span><span class="sxs-lookup"><span data-stu-id="84705-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="84705-108">取得值，指出兩個指定[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)執行個體會相等。</span><span class="sxs-lookup"><span data-stu-id="84705-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="84705-109">取得值，指出兩個指定的字串定義識別的表示是否相等。</span><span class="sxs-lookup"><span data-stu-id="84705-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="84705-110">取得值，指出兩個指定的字串參考識別表示法是否相等。</span><span class="sxs-lookup"><span data-stu-id="84705-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="84705-111">取得新的指標`IDefinitionIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="84705-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="84705-112">取得新的指標`IReferenceIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="84705-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="84705-113">取得指定的格式化的字串版`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="84705-114">填滿指定的字串版本指定寬字元緩衝區`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="84705-115">取得值，指出是否指定`IDefinitionIdentity`和`IReferenceIdentity`執行個體會參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="84705-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="84705-116">取得值，指出指定的字串是否參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="84705-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="84705-117">取得的指標，新建的字串索引鍵指定`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="84705-118">取得的指標，新建的字串索引鍵指定`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="84705-119">取得指定雜湊值`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="84705-120">取得指定雜湊值`IreferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="84705-121">取得指定的格式化的字串版`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="84705-122">填滿指定的字串版本指定寬字元緩衝區`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="84705-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="84705-123">取得的介面指標`IDefinitionIdentity`產生從指定的執行個體的格式字串。</span><span class="sxs-lookup"><span data-stu-id="84705-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="84705-124">取得的介面指標`IReferenceIdentity`產生從指定的執行個體的格式字串。</span><span class="sxs-lookup"><span data-stu-id="84705-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84705-125">需求</span><span class="sxs-lookup"><span data-stu-id="84705-125">Requirements</span></span>  
 <span data-ttu-id="84705-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84705-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84705-127">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="84705-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="84705-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84705-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84705-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84705-129">See Also</span></span>  
 [<span data-ttu-id="84705-130">融合介面</span><span class="sxs-lookup"><span data-stu-id="84705-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
