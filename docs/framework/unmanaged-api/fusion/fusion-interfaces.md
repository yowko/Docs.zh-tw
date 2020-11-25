---
title: 融合介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 59e34a39bada1dcf5e66a0c5b92a7fcbfb41d884
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711685"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="37c2d-102">融合介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-102">Fusion Interfaces</span></span>

<span data-ttu-id="37c2d-103">本節說明融合 API 用來存取應用程式資源屬性的非受控介面，以及為應用程式找出這些資源的正確版本。</span><span class="sxs-lookup"><span data-stu-id="37c2d-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37c2d-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="37c2d-104">In This Section</span></span>  

 [<span data-ttu-id="37c2d-105">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="37c2d-106">提供方法來產生和比較應用程式識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="37c2d-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="37c2d-107">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="37c2d-108">提供全域組件快取的標記法。</span><span class="sxs-lookup"><span data-stu-id="37c2d-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37c2d-109">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="37c2d-110">代表全域組件快取中的單一元件。</span><span class="sxs-lookup"><span data-stu-id="37c2d-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37c2d-111">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="37c2d-112">表示物件陣列的列舉值 `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="37c2d-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="37c2d-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="37c2d-114">提供用來描述和使用元件唯一身分識別的方法。</span><span class="sxs-lookup"><span data-stu-id="37c2d-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="37c2d-115">IDefinitionAppId 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="37c2d-116">表示在目前範圍中定義應用程式之程式碼的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="37c2d-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="37c2d-117">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="37c2d-118">表示在目前範圍中定義應用程式之程式碼的唯一簽章。</span><span class="sxs-lookup"><span data-stu-id="37c2d-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="37c2d-119">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="37c2d-120">作為物件集合的列舉值 `IDefinitionIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="37c2d-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="37c2d-121">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="37c2d-122">作為目前範圍中程式碼物件之屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="37c2d-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="37c2d-123">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="37c2d-124">作為物件集合的列舉值 `IReferenceIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="37c2d-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="37c2d-125">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="37c2d-126">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="37c2d-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="37c2d-127">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="37c2d-128">代表安裝在全域組件快取中參考元件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="37c2d-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37c2d-129">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="37c2d-130">代表安裝在全域組件快取中的專案。</span><span class="sxs-lookup"><span data-stu-id="37c2d-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37c2d-131">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="37c2d-132">代表目前範圍中應用程式之唯一識別碼的參考。</span><span class="sxs-lookup"><span data-stu-id="37c2d-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="37c2d-133">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="37c2d-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="37c2d-134">表示程式碼物件之唯一簽章的參考。</span><span class="sxs-lookup"><span data-stu-id="37c2d-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="37c2d-135">參考</span><span class="sxs-lookup"><span data-stu-id="37c2d-135">Reference</span></span>  

 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="37c2d-136">相關章節</span><span class="sxs-lookup"><span data-stu-id="37c2d-136">Related Sections</span></span>  

 [<span data-ttu-id="37c2d-137">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="37c2d-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="37c2d-138">融合列舉</span><span class="sxs-lookup"><span data-stu-id="37c2d-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="37c2d-139">融合結構</span><span class="sxs-lookup"><span data-stu-id="37c2d-139">Fusion Structures</span></span>](fusion-structures.md)
