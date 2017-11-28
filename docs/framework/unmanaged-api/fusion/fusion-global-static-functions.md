---
title: "融合全域靜態函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38462833e3b0ccd56265b02d9a1bc9f37ac12f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="0a1ee-102">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="0a1ee-103">本章節描述的 unmanaged 全域靜態函式融合 API 使用。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a1ee-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="0a1ee-104">In This Section</span></span>  
 [<span data-ttu-id="0a1ee-105">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="0a1ee-106">清除已下載組件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="0a1ee-107">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="0a1ee-108">比較兩個組件識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="0a1ee-109">CreateApplicationContext 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="0a1ee-110">僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-110">Internal only.</span></span> <span data-ttu-id="0a1ee-111">（這個函式支援.NET Framework 基礎結構和不適用於直接從程式碼）。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="0a1ee-112">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="0a1ee-113">取得新的指標[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)代表全域組件快取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="0a1ee-114">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="0a1ee-115">取得指標[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)執行個體，表示物件存在於指定的組件中的清單。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="0a1ee-116">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="0a1ee-117">取得指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)執行個體，表示具有指定名稱的組件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="0a1ee-118">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="0a1ee-119">建立指定的檔案歷程記錄讀取器。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="0a1ee-120">CreateInstallReferenceEnum 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="0a1ee-121">取得指標[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)執行個體，表示應用程式的參考指定組件的清單。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="0a1ee-122">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="0a1ee-123">取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式識別與參考索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="0a1ee-124">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="0a1ee-125">取得指標`IUnknown`物件具有指定`IID`中位於指定的檔案路徑的組件。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="0a1ee-126">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="0a1ee-127">取得使用指定的旗標的快取組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="0a1ee-128">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="0a1ee-129">擷取應用程式的歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="0a1ee-130">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="0a1ee-131">取得指標[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理程式碼物件的索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="0a1ee-132">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="0a1ee-133">取得值，指出指定的組件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="0a1ee-134">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="0a1ee-135">通用語言執行階段下載快取中刪除。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="0a1ee-136">PreBindAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="0a1ee-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="0a1ee-137">取得組件的原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="0a1ee-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a1ee-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="0a1ee-138">Related Sections</span></span>  
 [<span data-ttu-id="0a1ee-139">融合介面</span><span class="sxs-lookup"><span data-stu-id="0a1ee-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="0a1ee-140">融合列舉</span><span class="sxs-lookup"><span data-stu-id="0a1ee-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="0a1ee-141">融合結構</span><span class="sxs-lookup"><span data-stu-id="0a1ee-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="0a1ee-142">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="0a1ee-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
