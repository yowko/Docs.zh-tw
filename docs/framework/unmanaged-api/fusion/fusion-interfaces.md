---
title: 融合介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec2fd3b309820f2bfb7f6091cc3db720db497408
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697663"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="d2f86-102">融合介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-102">Fusion Interfaces</span></span>
<span data-ttu-id="d2f86-103">本章節描述融合 API 會使用存取的應用程式資源的屬性，並找出這些資源的應用程式的正確版本的 unmanaged 的介面。</span><span class="sxs-lookup"><span data-stu-id="d2f86-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2f86-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="d2f86-104">In This Section</span></span>  
 [<span data-ttu-id="d2f86-105">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="d2f86-106">提供方法，產生及比較應用程式身分識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d2f86-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="d2f86-107">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="d2f86-108">提供全域組件快取的表示法。</span><span class="sxs-lookup"><span data-stu-id="d2f86-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d2f86-109">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="d2f86-110">表示在全域組件快取中的單一組件。</span><span class="sxs-lookup"><span data-stu-id="d2f86-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d2f86-111">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="d2f86-112">表示陣列的列舉程式`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="d2f86-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="d2f86-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="d2f86-114">提供方法來描述和使用組件的唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="d2f86-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="d2f86-115">IDefinitionAppId 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="d2f86-116">代表目前範圍中定義應用程式的程式碼的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d2f86-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="d2f86-117">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="d2f86-118">代表目前範圍中定義應用程式的程式碼的唯一的簽章。</span><span class="sxs-lookup"><span data-stu-id="d2f86-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="d2f86-119">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="d2f86-120">做為集合的列舉值`IDefinitionIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="d2f86-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="d2f86-121">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="d2f86-122">可做為目前範圍中的程式碼物件的屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d2f86-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="d2f86-123">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="d2f86-124">做為集合的列舉程式`IReferenceIdentity`物件。</span><span class="sxs-lookup"><span data-stu-id="d2f86-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="d2f86-125">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="d2f86-126">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d2f86-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="d2f86-127">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="d2f86-128">表示參考的組件安裝在全域組件快取的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d2f86-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d2f86-129">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="d2f86-130">代表安裝在全域組件快取的項目。</span><span class="sxs-lookup"><span data-stu-id="d2f86-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="d2f86-131">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="d2f86-132">代表目前範圍中的應用程式的唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="d2f86-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="d2f86-133">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="d2f86-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="d2f86-134">表示唯一的簽章的程式碼物件的參考。</span><span class="sxs-lookup"><span data-stu-id="d2f86-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d2f86-135">參考資料</span><span class="sxs-lookup"><span data-stu-id="d2f86-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="d2f86-136">相關章節</span><span class="sxs-lookup"><span data-stu-id="d2f86-136">Related Sections</span></span>  
 [<span data-ttu-id="d2f86-137">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d2f86-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="d2f86-138">融合列舉</span><span class="sxs-lookup"><span data-stu-id="d2f86-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="d2f86-139">融合結構</span><span class="sxs-lookup"><span data-stu-id="d2f86-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
