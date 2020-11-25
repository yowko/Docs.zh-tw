---
title: ICLRRuntimeInfo 介面
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: 9f485728ddb050abf815bf8ba26c69be9c909785
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714966"
---
# <a name="iclrruntimeinfo-interface"></a><span data-ttu-id="6bb76-102">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6bb76-102">ICLRRuntimeInfo Interface</span></span>

<span data-ttu-id="6bb76-103">提供方法，以傳回特定 common language runtime (CLR) 的相關資訊，包括版本、目錄和載入狀態。</span><span class="sxs-lookup"><span data-stu-id="6bb76-103">Provides methods that return information about a specific common language runtime (CLR), including version, directory, and load status.</span></span> <span data-ttu-id="6bb76-104">這個介面也提供執行時間專屬的功能，而不需要初始化執行時間。</span><span class="sxs-lookup"><span data-stu-id="6bb76-104">This interface also provides runtime-specific functionality without initializing the runtime.</span></span> <span data-ttu-id="6bb76-105">它包含執行時間相關的 [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) 方法、執行時間模組特定的 [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) 方法，以及透過 [GetInterface](iclrruntimeinfo-getinterface-method.md) 方法提供的執行時間介面。</span><span class="sxs-lookup"><span data-stu-id="6bb76-105">It includes the runtime-relative [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method, the runtime module-specific [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method, and runtime-provided interfaces through the [GetInterface](iclrruntimeinfo-getinterface-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bb76-106">方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-106">Methods</span></span>  
  
|<span data-ttu-id="6bb76-107">方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-107">Method</span></span>|<span data-ttu-id="6bb76-108">描述</span><span class="sxs-lookup"><span data-stu-id="6bb76-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bb76-109">BindAsLegacyV2Runtime 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-109">BindAsLegacyV2Runtime Method</span></span>](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|<span data-ttu-id="6bb76-110">將此執行時間系結到所有舊版 CLR 第2版啟用原則決策。</span><span class="sxs-lookup"><span data-stu-id="6bb76-110">Binds this runtime for all legacy CLR version 2 activation policy decisions.</span></span>|  
|[<span data-ttu-id="6bb76-111">GetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-111">GetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-getdefaultstartupflags-method.md)|<span data-ttu-id="6bb76-112">取得 CLR 啟動旗標和主機設定檔案。</span><span class="sxs-lookup"><span data-stu-id="6bb76-112">Gets the CLR startup flags and host configuration file.</span></span>|  
|[<span data-ttu-id="6bb76-113">GetInterface 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-113">GetInterface Method</span></span>](iclrruntimeinfo-getinterface-method.md)|<span data-ttu-id="6bb76-114">將 CLR 載入目前的進程，並傳回執行時間介面指標，例如 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md) 和 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6bb76-114">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) and [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md).</span></span> <span data-ttu-id="6bb76-115">這個方法會取代所有的函式 `CorBindTo*` 。</span><span class="sxs-lookup"><span data-stu-id="6bb76-115">This method supersedes all the `CorBindTo*` functions.</span></span>|  
|[<span data-ttu-id="6bb76-116">GetProcAddress 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-116">GetProcAddress Method</span></span>](iclrruntimeinfo-getprocaddress-method.md)|<span data-ttu-id="6bb76-117">取得從與這個介面相關聯的 CLR 匯出之指定函式的位址。</span><span class="sxs-lookup"><span data-stu-id="6bb76-117">Gets the address of a specified function that was exported from the CLR associated with this interface.</span></span> <span data-ttu-id="6bb76-118">這個方法會取代 [GetRealProcAddress](getrealprocaddress-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6bb76-118">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) method.</span></span>|  
|[<span data-ttu-id="6bb76-119">GetRuntimeDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-119">GetRuntimeDirectory Method</span></span>](iclrruntimeinfo-getruntimedirectory-method.md)|<span data-ttu-id="6bb76-120">取得與此介面相關聯之 CLR 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="6bb76-120">Gets the installation directory of the CLR associated with this interface.</span></span> <span data-ttu-id="6bb76-121">這個方法會取代 [GetCORSystemDirectory](getcorsystemdirectory-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6bb76-121">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) method.</span></span>|  
|[<span data-ttu-id="6bb76-122">GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-122">GetVersionString Method</span></span>](iclrruntimeinfo-getversionstring-method.md)|<span data-ttu-id="6bb76-123">取得與給定 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 common language RUNTIME (CLR) 版本資訊。</span><span class="sxs-lookup"><span data-stu-id="6bb76-123">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="6bb76-124">這個方法會取代 [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) 和 [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6bb76-124">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) and [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) methods.</span></span>|  
|[<span data-ttu-id="6bb76-125">IsLoadable 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-125">IsLoadable Method</span></span>](iclrruntimeinfo-isloadable-method.md)|<span data-ttu-id="6bb76-126">指出與這個介面相關聯的執行時間是否可以載入至目前的進程，並將可能已載入至進程的其他執行時間納入考慮。</span><span class="sxs-lookup"><span data-stu-id="6bb76-126">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>|  
|[<span data-ttu-id="6bb76-127">IsLoaded 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-127">IsLoaded Method</span></span>](iclrruntimeinfo-isloaded-method.md)|<span data-ttu-id="6bb76-128">指出與 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 CLR 是否會載入至進程。</span><span class="sxs-lookup"><span data-stu-id="6bb76-128">Indicates whether the CLR associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span>|  
|[<span data-ttu-id="6bb76-129">IsStarted 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-129">IsStarted Method</span></span>](iclrruntimeinfo-isstarted-method.md)|<span data-ttu-id="6bb76-130">指出與 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 CLR 是否已啟動。</span><span class="sxs-lookup"><span data-stu-id="6bb76-130">Indicates whether the CLR that is associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface has been started.</span></span>|  
|[<span data-ttu-id="6bb76-131">LoadErrorString 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-131">LoadErrorString Method</span></span>](iclrruntimeinfo-loaderrorstring-method.md)|<span data-ttu-id="6bb76-132">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="6bb76-132">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span> <span data-ttu-id="6bb76-133">這個方法會取代 [LoadStringRC](loadstringrc-function.md) 和 [LoadStringRCEx](loadstringrcex-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6bb76-133">This method supersedes the [LoadStringRC](loadstringrc-function.md) and [LoadStringRCEx](loadstringrcex-function.md) methods.</span></span>|  
|[<span data-ttu-id="6bb76-134">LoadLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-134">LoadLibrary Method</span></span>](iclrruntimeinfo-loadlibrary-method.md)|<span data-ttu-id="6bb76-135">從 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面所代表之 CLR 的 framework 目錄載入程式庫。</span><span class="sxs-lookup"><span data-stu-id="6bb76-135">Loads a library from the framework directory of the CLR represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="6bb76-136">這個方法會取代 [LoadLibraryShim](loadlibraryshim-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="6bb76-136">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) method.</span></span>|  
|[<span data-ttu-id="6bb76-137">SetDefaultStartupFlags 方法</span><span class="sxs-lookup"><span data-stu-id="6bb76-137">SetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-setdefaultstartupflags-method.md)|<span data-ttu-id="6bb76-138">設定 CLR 啟動旗標和主機設定檔案。</span><span class="sxs-lookup"><span data-stu-id="6bb76-138">Sets the CLR startup flags and host configuration file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bb76-139">需求</span><span class="sxs-lookup"><span data-stu-id="6bb76-139">Requirements</span></span>  

 <span data-ttu-id="6bb76-140">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bb76-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb76-141">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="6bb76-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6bb76-142">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6bb76-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bb76-143">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb76-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb76-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bb76-144">See also</span></span>

- [<span data-ttu-id="6bb76-145">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6bb76-145">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6bb76-146">裝載</span><span class="sxs-lookup"><span data-stu-id="6bb76-146">Hosting</span></span>](index.md)
