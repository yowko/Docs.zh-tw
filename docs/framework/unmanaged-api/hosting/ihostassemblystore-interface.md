---
title: IHostAssemblyStore 介面
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3714f31d0ab58584a8671055cf4c607f04a832c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611055"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="d0249-102">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="d0249-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="d0249-103">提供方法，可讓主應用程式載入組件和模組與 common language runtime (CLR) 無關。</span><span class="sxs-lookup"><span data-stu-id="d0249-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0249-104">方法</span><span class="sxs-lookup"><span data-stu-id="d0249-104">Methods</span></span>  
  
|<span data-ttu-id="d0249-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0249-105">Method</span></span>|<span data-ttu-id="d0249-106">描述</span><span class="sxs-lookup"><span data-stu-id="d0249-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0249-107">ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="d0249-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="d0249-108">取得未參考的組件的參考[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從呼叫傳回[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d0249-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="d0249-109">ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="d0249-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="d0249-110">解析組件或連結的 （未內嵌） 的資源檔內的模組。</span><span class="sxs-lookup"><span data-stu-id="d0249-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0249-111">備註</span><span class="sxs-lookup"><span data-stu-id="d0249-111">Remarks</span></span>  
 <span data-ttu-id="d0249-112">`IHostAssemblyStore` 可讓主應用程式載入有效的組件識別為基礎的組件。</span><span class="sxs-lookup"><span data-stu-id="d0249-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="d0249-113">主應用程式載入的組件，藉由傳回`IStream`直接指向位元組的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0249-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="d0249-114">CLR 可讓您判斷主機是否已實作`IHostAssemblyStore`藉由呼叫`IHostAssemblyManager::GetNonHostAssemblyStores`初始化時。</span><span class="sxs-lookup"><span data-stu-id="d0249-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="d0249-115">這可讓主應用程式，例如，控制繫結至使用者的組件，而是依賴執行階段繫結至.NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="d0249-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0249-116">提供實作`IHostAssemblyStore`，主應用程式指定解析所有組件，不會參考其意圖`ICLRAssemblyReferenceList`傳回`IHostAssemblyManager::GetNonHostStoreAssemblies`。</span><span class="sxs-lookup"><span data-stu-id="d0249-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0249-117">.NET Framework 2.0 版不提供主應用程式載入的組件，原生映像的方式，提供[原生映像產生器 (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)公用程式。</span><span class="sxs-lookup"><span data-stu-id="d0249-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0249-118">需求</span><span class="sxs-lookup"><span data-stu-id="d0249-118">Requirements</span></span>  
 <span data-ttu-id="d0249-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0249-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0249-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0249-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0249-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0249-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0249-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0249-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0249-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0249-123">See also</span></span>
- [<span data-ttu-id="d0249-124">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="d0249-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d0249-125">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="d0249-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d0249-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d0249-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
