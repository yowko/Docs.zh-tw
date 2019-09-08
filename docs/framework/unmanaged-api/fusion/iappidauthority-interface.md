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
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796834"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="c401f-102">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="c401f-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="c401f-103">提供方法，以產生並比較應用程式識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c401f-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c401f-104">方法</span><span class="sxs-lookup"><span data-stu-id="c401f-104">Methods</span></span>  
  
|<span data-ttu-id="c401f-105">方法</span><span class="sxs-lookup"><span data-stu-id="c401f-105">Method</span></span>|<span data-ttu-id="c401f-106">說明</span><span class="sxs-lookup"><span data-stu-id="c401f-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="c401f-107">取得值，指出兩個指定的[IDefinitionAppId](idefinitionappid-interface.md)實例是否相等。</span><span class="sxs-lookup"><span data-stu-id="c401f-107">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="c401f-108">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c401f-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="c401f-109">取得值，指出兩個指定的[IReferenceAppId](ireferenceappid-interface.md)實例是否相等。</span><span class="sxs-lookup"><span data-stu-id="c401f-109">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="c401f-110">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c401f-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="c401f-111">取得值，指出兩個指定的字串定義是否相等。</span><span class="sxs-lookup"><span data-stu-id="c401f-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="c401f-112">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c401f-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="c401f-113">取得值，指出兩個指定的字串參考是否相等。</span><span class="sxs-lookup"><span data-stu-id="c401f-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="c401f-114">您可以傳遞旗標值 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION 來忽略其各自的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c401f-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="c401f-115">取得新產生`IDefinitionAppId`之實例的介面指標，表示目前範圍中的元件。</span><span class="sxs-lookup"><span data-stu-id="c401f-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="c401f-116">取得新建立`IReferenceAppId`的介面指標，其代表目前範圍中的元件。</span><span class="sxs-lookup"><span data-stu-id="c401f-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="c401f-117">使用指定的旗標值， `IDefinitionAppId`取得指定的的字串版本。</span><span class="sxs-lookup"><span data-stu-id="c401f-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="c401f-118">取得值，指出指定`IDefinitionAppId`的和`IReferenceAppId`是否表示相同的元件。</span><span class="sxs-lookup"><span data-stu-id="c401f-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="c401f-119">取得值，指出指定的定義字串和參考字串是否代表相同的元件。</span><span class="sxs-lookup"><span data-stu-id="c401f-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="c401f-120">取得表示指定`IDefinitionAppId`之實例的字串索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c401f-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="c401f-121">取得表示指定`IReferenceAppId`之實例的字串索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c401f-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="c401f-122">取得指定`IDefinitionAppId`之實例的雜湊索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c401f-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="c401f-123">取得指定`IReferenceAppId`之實例的雜湊索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c401f-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="c401f-124">使用指定的旗標值， `IReferenceAppId`取得指定的的字串版本。</span><span class="sxs-lookup"><span data-stu-id="c401f-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="c401f-125">取得`IDefinitionAppId`實例的介面指標，表示指定的字串索引鍵所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="c401f-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="c401f-126">取得`IReferenceAppId`實例的介面指標，表示指定的字串索引鍵所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="c401f-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c401f-127">需求</span><span class="sxs-lookup"><span data-stu-id="c401f-127">Requirements</span></span>  
 <span data-ttu-id="c401f-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c401f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c401f-129">**標頭：** 隔離。h</span><span class="sxs-lookup"><span data-stu-id="c401f-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c401f-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c401f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c401f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c401f-131">See also</span></span>

- [<span data-ttu-id="c401f-132">融合介面</span><span class="sxs-lookup"><span data-stu-id="c401f-132">Fusion Interfaces</span></span>](fusion-interfaces.md)
