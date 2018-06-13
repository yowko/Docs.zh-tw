---
title: IAppIdAuthority 介面
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433746"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="e593f-102">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="e593f-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="e593f-103">提供方法，產生並比較應用程式的身分識別與參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e593f-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e593f-104">方法</span><span class="sxs-lookup"><span data-stu-id="e593f-104">Methods</span></span>  
  
|<span data-ttu-id="e593f-105">方法</span><span class="sxs-lookup"><span data-stu-id="e593f-105">Method</span></span>|<span data-ttu-id="e593f-106">描述</span><span class="sxs-lookup"><span data-stu-id="e593f-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="e593f-107">取得值，指出兩個指定[IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)執行個體會相等。</span><span class="sxs-lookup"><span data-stu-id="e593f-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="e593f-108">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="e593f-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="e593f-109">取得值，指出兩個指定[IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)執行個體會相等。</span><span class="sxs-lookup"><span data-stu-id="e593f-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="e593f-110">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="e593f-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="e593f-111">取得值，指出兩個指定的字串定義是否相等。</span><span class="sxs-lookup"><span data-stu-id="e593f-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="e593f-112">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="e593f-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="e593f-113">取得值，指出兩個指定的字串參考是否相等。</span><span class="sxs-lookup"><span data-stu-id="e593f-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="e593f-114">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 略過其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="e593f-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="e593f-115">取得新產生的介面指標`IDefinitionAppId`代表目前範圍中的組件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="e593f-116">取得的介面指標，新建`IReferenceAppId`，代表目前範圍中的組件。</span><span class="sxs-lookup"><span data-stu-id="e593f-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="e593f-117">取得指定的字串版本`IDefinitionAppId`，使用指定的旗標值。</span><span class="sxs-lookup"><span data-stu-id="e593f-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="e593f-118">取得值，指出是否指定`IDefinitionAppId`和`IReferenceAppId`代表相同的組件。</span><span class="sxs-lookup"><span data-stu-id="e593f-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="e593f-119">取得值，指出指定的定義字串和參考字串是否表示相同的組件。</span><span class="sxs-lookup"><span data-stu-id="e593f-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="e593f-120">取得代表指定的字串索引鍵`IDefinitionAppId`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="e593f-121">取得代表指定的字串索引鍵`IReferenceAppId`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="e593f-122">取得所指定的雜湊索引鍵`IDefinitionAppId`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="e593f-123">取得所指定的雜湊索引鍵`IReferenceAppId`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="e593f-124">取得指定的字串版本`IReferenceAppId`，使用指定的旗標值。</span><span class="sxs-lookup"><span data-stu-id="e593f-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="e593f-125">取得的介面指標`IDefinitionAppId`表示的指定的字串索引鍵參考的組件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="e593f-126">取得的介面指標`IReferenceAppId`表示的指定的字串索引鍵參考的組件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e593f-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e593f-127">需求</span><span class="sxs-lookup"><span data-stu-id="e593f-127">Requirements</span></span>  
 <span data-ttu-id="e593f-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e593f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e593f-129">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e593f-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e593f-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e593f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e593f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e593f-131">See Also</span></span>  
 [<span data-ttu-id="e593f-132">融合介面</span><span class="sxs-lookup"><span data-stu-id="e593f-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
