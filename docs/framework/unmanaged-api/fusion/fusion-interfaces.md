---
title: 融合介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 81c66825e69d9526abddfe06133426a2274ad08f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108187"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="41fef-102">融合介面</span><span class="sxs-lookup"><span data-stu-id="41fef-102">Fusion Interfaces</span></span>
<span data-ttu-id="41fef-103">本節說明融合 API 用來存取應用程式資源屬性的非受控介面，以及為應用程式找出這些資源的正確版本。</span><span class="sxs-lookup"><span data-stu-id="41fef-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41fef-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="41fef-104">In This Section</span></span>  
 [<span data-ttu-id="41fef-105">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="41fef-106">提供方法，以產生並比較應用程式識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="41fef-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="41fef-107">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="41fef-108">提供全域組件快取的標記法。</span><span class="sxs-lookup"><span data-stu-id="41fef-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="41fef-109">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="41fef-110">代表全域組件快取中的單一元件。</span><span class="sxs-lookup"><span data-stu-id="41fef-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="41fef-111">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="41fef-112">表示 `IAssemblyName` 物件陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="41fef-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="41fef-113">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="41fef-114">提供方法來描述和使用元件的唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="41fef-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="41fef-115">IDefinitionAppId 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="41fef-116">表示在目前範圍中定義應用程式之程式碼的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="41fef-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="41fef-117">IDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="41fef-118">表示在目前範圍中定義應用程式之程式碼的唯一簽章。</span><span class="sxs-lookup"><span data-stu-id="41fef-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="41fef-119">IEnumDefinitionIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="41fef-120">作為 `IDefinitionIdentity` 物件集合的列舉值。</span><span class="sxs-lookup"><span data-stu-id="41fef-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="41fef-121">IEnumIDENTITY_ATTRIBUTE 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="41fef-122">作為目前範圍中程式碼物件屬性的列舉值。</span><span class="sxs-lookup"><span data-stu-id="41fef-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="41fef-123">IEnumReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="41fef-124">作為 `IReferenceIdentity` 物件集合的列舉值。</span><span class="sxs-lookup"><span data-stu-id="41fef-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="41fef-125">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="41fef-126">管理程式碼物件的識別索引鍵。</span><span class="sxs-lookup"><span data-stu-id="41fef-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="41fef-127">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="41fef-128">代表安裝在全域組件快取中參考元件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="41fef-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="41fef-129">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="41fef-130">代表安裝在全域組件快取中的專案。</span><span class="sxs-lookup"><span data-stu-id="41fef-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="41fef-131">IReferenceAppId 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="41fef-132">代表目前範圍中應用程式的唯一識別碼參考。</span><span class="sxs-lookup"><span data-stu-id="41fef-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="41fef-133">IReferenceIdentity 介面</span><span class="sxs-lookup"><span data-stu-id="41fef-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="41fef-134">表示程式碼物件之唯一簽章的參考。</span><span class="sxs-lookup"><span data-stu-id="41fef-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41fef-135">參考資料</span><span class="sxs-lookup"><span data-stu-id="41fef-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="41fef-136">相關章節</span><span class="sxs-lookup"><span data-stu-id="41fef-136">Related Sections</span></span>  
 [<span data-ttu-id="41fef-137">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="41fef-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="41fef-138">融合列舉</span><span class="sxs-lookup"><span data-stu-id="41fef-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="41fef-139">融合結構</span><span class="sxs-lookup"><span data-stu-id="41fef-139">Fusion Structures</span></span>](fusion-structures.md)
