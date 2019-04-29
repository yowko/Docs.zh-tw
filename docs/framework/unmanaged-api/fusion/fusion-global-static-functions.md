---
title: 融合全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697715"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="a1b6f-102">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="a1b6f-103">本節說明的 unmanaged 全域靜態函式融合 API 使用。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1b6f-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="a1b6f-104">In This Section</span></span>  
 [<span data-ttu-id="a1b6f-105">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="a1b6f-106">清除已下載的組件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="a1b6f-107">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="a1b6f-108">比較兩個組件身分識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="a1b6f-109">CreateApplicationContext 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="a1b6f-110">僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-110">Internal only.</span></span> <span data-ttu-id="a1b6f-111">（此函式支援.NET Framework 基礎結構並不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="a1b6f-112">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="a1b6f-113">取得新指標[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)表示全域組件快取執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="a1b6f-114">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="a1b6f-115">取得指標[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)執行個體，表示物件存在於指定的組件中的清單。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="a1b6f-116">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="a1b6f-117">取得指標[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)執行個體，表示具有指定名稱的組件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="a1b6f-118">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="a1b6f-119">建立記錄讀取器指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="a1b6f-120">CreateInstallReferenceEnum 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="a1b6f-121">取得指標[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)執行個體，表示指定的組件的應用程式的參考清單。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="a1b6f-122">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="a1b6f-123">取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式身分識別和參考的索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="a1b6f-124">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="a1b6f-125">取得指標`IUnknown`使用指定的物件`IID`中指定的檔案路徑中的組件。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="a1b6f-126">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="a1b6f-127">取得快取的組件，並使用指定的旗標的路徑。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="a1b6f-128">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="a1b6f-129">擷取應用程式記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="a1b6f-130">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="a1b6f-131">取得指標[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理程式碼物件的索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="a1b6f-132">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="a1b6f-133">取得值，指出指定的組件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="a1b6f-134">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="a1b6f-135">刪除通用語言執行階段下載快取。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="a1b6f-136">PreBindAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="a1b6f-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="a1b6f-137">取得組件的原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a1b6f-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1b6f-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="a1b6f-138">Related Sections</span></span>  
 [<span data-ttu-id="a1b6f-139">融合介面</span><span class="sxs-lookup"><span data-stu-id="a1b6f-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="a1b6f-140">融合列舉</span><span class="sxs-lookup"><span data-stu-id="a1b6f-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="a1b6f-141">融合結構</span><span class="sxs-lookup"><span data-stu-id="a1b6f-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="a1b6f-142">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="a1b6f-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
