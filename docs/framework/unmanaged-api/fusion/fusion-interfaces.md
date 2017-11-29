---
title: "融合介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1742025bed977dfd377a78db42df42c1bc43966
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-interfaces"></a><span data-ttu-id="1c813-102">融合介面</span><span class="sxs-lookup"><span data-stu-id="1c813-102">Fusion Interfaces</span></span>
<span data-ttu-id="1c813-103">本章節描述融合 API 會使用來存取應用程式的資源的內容，並找出正確的版本的應用程式資源的 unmanaged 的介面。</span><span class="sxs-lookup"><span data-stu-id="1c813-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c813-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1c813-104">In This Section</span></span>  
 [<span data-ttu-id="1c813-105">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="1c813-106">提供方法，產生並比較應用程式的身分識別與參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1c813-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="1c813-107">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="1c813-108">提供全域組件快取的表示法。</span><span class="sxs-lookup"><span data-stu-id="1c813-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="1c813-109">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="1c813-110">表示在全域組件快取中的單一組件。</span><span class="sxs-lookup"><span data-stu-id="1c813-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="1c813-111">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="1c813-112">表示陣列的列舉值`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="1c813-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="1c813-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="1c813-114">提供方法來描述及使用組件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="1c813-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="1c813-115">IDefinitionAppId 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="1c813-116">代表目前範圍中定義的應用程式的程式碼的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1c813-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="1c813-117">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="1c813-118">代表目前範圍中定義的應用程式的程式碼的唯一的簽章。</span><span class="sxs-lookup"><span data-stu-id="1c813-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="1c813-119">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="1c813-120">做為集合的列舉值`IDefinitionIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="1c813-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="1c813-121">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="1c813-122">可做為目前範圍中的程式碼物件的屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1c813-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="1c813-123">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="1c813-124">做為集合的列舉值`IReferenceIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="1c813-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="1c813-125">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="1c813-126">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1c813-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="1c813-127">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="1c813-128">代表安裝在全域組件快取的參考組件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1c813-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="1c813-129">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="1c813-130">代表安裝在全域組件快取的項目。</span><span class="sxs-lookup"><span data-stu-id="1c813-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="1c813-131">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="1c813-132">代表目前範圍中的應用程式的唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="1c813-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="1c813-133">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="1c813-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="1c813-134">表示唯一的簽章的程式碼物件的參考。</span><span class="sxs-lookup"><span data-stu-id="1c813-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c813-135">參考資料</span><span class="sxs-lookup"><span data-stu-id="1c813-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="1c813-136">相關章節</span><span class="sxs-lookup"><span data-stu-id="1c813-136">Related Sections</span></span>  
 [<span data-ttu-id="1c813-137">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="1c813-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="1c813-138">融合列舉</span><span class="sxs-lookup"><span data-stu-id="1c813-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="1c813-139">融合結構</span><span class="sxs-lookup"><span data-stu-id="1c813-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
