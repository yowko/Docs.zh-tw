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
ms.openlocfilehash: 263dc0f9d686440aaa23e359c26db1b4d3d09b1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609096"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="e2582-102">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="e2582-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="e2582-103">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e2582-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="e2582-104">方法</span><span class="sxs-lookup"><span data-stu-id="e2582-104">Methods</span></span>

|<span data-ttu-id="e2582-105">方法</span><span class="sxs-lookup"><span data-stu-id="e2582-105">Method</span></span>|<span data-ttu-id="e2582-106">描述</span><span class="sxs-lookup"><span data-stu-id="e2582-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="e2582-107">取得值，指出兩個指定是否[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)執行個體是否相等。</span><span class="sxs-lookup"><span data-stu-id="e2582-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="e2582-108">取得值，指出兩個指定是否[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)執行個體是否相等。</span><span class="sxs-lookup"><span data-stu-id="e2582-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="e2582-109">取得值，指出兩個指定的字串定義識別表示法是否相等。</span><span class="sxs-lookup"><span data-stu-id="e2582-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="e2582-110">取得值，指出兩個指定的字串參考身分識別表示法是否相等。</span><span class="sxs-lookup"><span data-stu-id="e2582-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="e2582-111">取得新的指標`IDefinitionIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2582-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="e2582-112">取得新的指標`IReferenceIdentity`代表目前範圍中的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2582-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="e2582-113">取得指定的格式化的字串版本`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="e2582-114">填滿指定的字串版本指定寬字元的緩衝區`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="e2582-115">取得值，指出是否指定`IDefinitionIdentity`和`IReferenceIdentity`參考相同的程式碼物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2582-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="e2582-116">取得值，指出指定的字串是否參考相同的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="e2582-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="e2582-117">取得指定之新建立的字串索引鍵的指標`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="e2582-118">取得指定之新建立的字串索引鍵的指標`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="e2582-119">取得所指定的雜湊值`IDefinitionIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="e2582-120">取得所指定的雜湊值`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="e2582-121">取得指定的格式化的字串版本`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="e2582-122">填滿指定的字串版本指定寬字元的緩衝區`IReferenceIdentity`。</span><span class="sxs-lookup"><span data-stu-id="e2582-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="e2582-123">取得的介面指標`IDefinitionIdentity`產生從指定的執行個體格式化字串。</span><span class="sxs-lookup"><span data-stu-id="e2582-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="e2582-124">取得的介面指標`IReferenceIdentity`產生從指定的執行個體格式化字串。</span><span class="sxs-lookup"><span data-stu-id="e2582-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="e2582-125">需求</span><span class="sxs-lookup"><span data-stu-id="e2582-125">Requirements</span></span>

<span data-ttu-id="e2582-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2582-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e2582-127">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e2582-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="e2582-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2582-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e2582-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2582-129">See also</span></span>

- [<span data-ttu-id="e2582-130">融合介面</span><span class="sxs-lookup"><span data-stu-id="e2582-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
