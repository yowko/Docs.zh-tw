---
title: 融合全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: 691fd50e05cadd3f82196fc6ba5df9bb84a66faa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688740"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="22a56-102">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="22a56-102">Fusion Global Static Functions</span></span>

<span data-ttu-id="22a56-103">本節說明融合 API 所使用的非受控全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="22a56-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22a56-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="22a56-104">In This Section</span></span>  

 [<span data-ttu-id="22a56-105">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="22a56-106">清除已下載元件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="22a56-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="22a56-107">CompareAssemblyIdentity 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="22a56-108">比較兩個元件身分識別，以判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="22a56-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="22a56-109">CreateApplicationContext 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="22a56-110">僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="22a56-110">Internal only.</span></span> <span data-ttu-id="22a56-111"> (此函式支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 ) </span><span class="sxs-lookup"><span data-stu-id="22a56-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="22a56-112">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="22a56-113">取得代表全域組件快取之新 [IAssemblyCache](iassemblycache-interface.md) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="22a56-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="22a56-114">CreateAssemblyEnum 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="22a56-115">取得 [IAssemblyEnum](iassemblyenum-interface.md) 實例的指標，該實例表示存在於指定元件中的物件清單。</span><span class="sxs-lookup"><span data-stu-id="22a56-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="22a56-116">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="22a56-117">取得 [IAssemblyName](iassemblyname-interface.md) 實例的指標，該實例表示具有指定名稱之元件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="22a56-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="22a56-118">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="22a56-119">為指定的檔案建立歷程記錄讀取器。</span><span class="sxs-lookup"><span data-stu-id="22a56-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="22a56-120">CreateInstallReferenceEnum 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="22a56-121">取得 [IInstallReferenceEnum](iinstallreferenceenum-interface.md) 實例的指標，該實例表示應用程式對指定元件的參考清單。</span><span class="sxs-lookup"><span data-stu-id="22a56-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="22a56-122">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="22a56-123">取得 [IAppIdAuthority](iappidauthority-interface.md) 實例的指標，該實例會管理應用程式識別和參考的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="22a56-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="22a56-124">GetAssemblyIdentityFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="22a56-125">取得物件的指標，該 `IUnknown` 物件具有在 `IID` 指定檔案路徑的元件中指定的。</span><span class="sxs-lookup"><span data-stu-id="22a56-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="22a56-126">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="22a56-127">使用指定的旗標，取得快取元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="22a56-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="22a56-128">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="22a56-129">抓取應用程式歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="22a56-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="22a56-130">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="22a56-131">取得 [IIdentityAuthority](iidentityauthority-interface.md) 實例的指標，該實例會管理程式碼物件的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="22a56-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="22a56-132">IsFrameworkAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="22a56-133">取得值，這個值會指出指定的元件是否為 managed。</span><span class="sxs-lookup"><span data-stu-id="22a56-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="22a56-134">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="22a56-135">刪除 common language runtime 下載快取。</span><span class="sxs-lookup"><span data-stu-id="22a56-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="22a56-136">PreBindAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="22a56-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="22a56-137">取得元件的原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="22a56-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="22a56-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="22a56-138">Related Sections</span></span>  

 [<span data-ttu-id="22a56-139">融合介面</span><span class="sxs-lookup"><span data-stu-id="22a56-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="22a56-140">融合列舉</span><span class="sxs-lookup"><span data-stu-id="22a56-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="22a56-141">融合結構</span><span class="sxs-lookup"><span data-stu-id="22a56-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="22a56-142">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="22a56-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
