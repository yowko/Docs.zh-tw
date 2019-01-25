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
ms.openlocfilehash: ab8965ca5d6c9c96cea5f5b351547ce2d4dfacc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546276"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="22ab8-102">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="22ab8-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="22ab8-103">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="22ab8-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22ab8-104">方法</span><span class="sxs-lookup"><span data-stu-id="22ab8-104">Methods</span></span>  
  
|<span data-ttu-id="22ab8-105">方法</span><span class="sxs-lookup"><span data-stu-id="22ab8-105">Method</span></span>|<span data-ttu-id="22ab8-106">描述</span><span class="sxs-lookup"><span data-stu-id="22ab8-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="22ab8-107">取得值，指出兩個指定是否[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體是否相等。</span><span class="sxs-lookup"><span data-stu-id="22ab8-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="22ab8-108">取得值，指出兩個指定是否[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)執行個體是否相等。</span><span class="sxs-lookup"><span data-stu-id="22ab8-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="22ab8-109">取得值，指出兩個指定的字串定義識別表示法是否相等。</span><span class="sxs-lookup"><span data-stu-id="22ab8-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="22ab8-110">取得值，指出兩個指定的字串參考身分識別表示法是否相等。</span><span class="sxs-lookup"><span data-stu-id="22ab8-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="22ab8-111">取得新的指標`IDefinitionIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="22ab8-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="22ab8-112">取得新的指標`IReferenceIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="22ab8-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="22ab8-113">取得指定的格式化的字串版本`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="22ab8-114">填滿指定的字串版本指定寬字元的緩衝區`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="22ab8-115">取得值，指出是否指定`IDefinitionIdentity`和`IReferenceIdentity`參考相同的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="22ab8-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="22ab8-116">取得值，指出指定的字串是否參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="22ab8-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="22ab8-117">取得指定之新建立的字串索引鍵的指標`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="22ab8-118">取得指定之新建立的字串索引鍵的指標`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="22ab8-119">取得所指定的雜湊值`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="22ab8-120">取得所指定的雜湊值`IreferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="22ab8-121">取得指定的格式化的字串版本`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="22ab8-122">填滿指定的字串版本指定寬字元的緩衝區`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="22ab8-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="22ab8-123">取得的介面指標`IDefinitionIdentity`產生從指定的執行個體格式化字串。</span><span class="sxs-lookup"><span data-stu-id="22ab8-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="22ab8-124">取得的介面指標`IReferenceIdentity`產生從指定的執行個體格式化字串。</span><span class="sxs-lookup"><span data-stu-id="22ab8-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22ab8-125">需求</span><span class="sxs-lookup"><span data-stu-id="22ab8-125">Requirements</span></span>  
 <span data-ttu-id="22ab8-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22ab8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22ab8-127">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="22ab8-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="22ab8-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22ab8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ab8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22ab8-129">See also</span></span>
- [<span data-ttu-id="22ab8-130">融合介面</span><span class="sxs-lookup"><span data-stu-id="22ab8-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
