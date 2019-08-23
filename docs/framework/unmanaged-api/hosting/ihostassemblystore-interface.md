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
ms.openlocfilehash: f881440b2e93745723bd090cfbab0286dcd0a4e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937867"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="4fa96-102">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="4fa96-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="4fa96-103">提供的方法可讓主機獨立載入元件和模組, 而不受 common language runtime (CLR) 的影響。</span><span class="sxs-lookup"><span data-stu-id="4fa96-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fa96-104">方法</span><span class="sxs-lookup"><span data-stu-id="4fa96-104">Methods</span></span>  
  
|<span data-ttu-id="4fa96-105">方法</span><span class="sxs-lookup"><span data-stu-id="4fa96-105">Method</span></span>|<span data-ttu-id="4fa96-106">描述</span><span class="sxs-lookup"><span data-stu-id="4fa96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fa96-107">ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="4fa96-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="4fa96-108">取得對[IHostAssemblyManager:: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)的呼叫所傳回之[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)未參考的元件參考。</span><span class="sxs-lookup"><span data-stu-id="4fa96-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="4fa96-109">ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="4fa96-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="4fa96-110">解析元件或連結 (非內嵌) 資源檔內的模組。</span><span class="sxs-lookup"><span data-stu-id="4fa96-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fa96-111">備註</span><span class="sxs-lookup"><span data-stu-id="4fa96-111">Remarks</span></span>  
 <span data-ttu-id="4fa96-112">`IHostAssemblyStore`提供一種方式, 讓主機根據元件識別有效率地載入元件。</span><span class="sxs-lookup"><span data-stu-id="4fa96-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="4fa96-113">主機會藉由`IStream`傳回直接指向位元組的實例來載入元件。</span><span class="sxs-lookup"><span data-stu-id="4fa96-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="4fa96-114">CLR 會藉由在初始化時呼叫`IHostAssemblyStore` `IHostAssemblyManager::GetNonHostAssemblyStores`來判斷主機是否已執行。</span><span class="sxs-lookup"><span data-stu-id="4fa96-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="4fa96-115">例如, 這可讓主機控制使用者元件的系結, 但依賴執行時間來系結至 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="4fa96-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fa96-116">在提供的`IHostAssemblyStore`執行時, 主機會指定其目的, 以解析傳回之`IHostAssemblyManager::GetNonHostStoreAssemblies`所參考的`ICLRAssemblyReferenceList`所有元件。</span><span class="sxs-lookup"><span data-stu-id="4fa96-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fa96-117">.NET Framework 版本2.0 不會提供方法, 讓主機載入元件的原生映射, 如同[原生映射產生器 (ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)公用程式所提供。</span><span class="sxs-lookup"><span data-stu-id="4fa96-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa96-118">需求</span><span class="sxs-lookup"><span data-stu-id="4fa96-118">Requirements</span></span>  
 <span data-ttu-id="4fa96-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa96-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa96-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4fa96-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fa96-121">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4fa96-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fa96-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa96-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa96-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa96-123">See also</span></span>

- [<span data-ttu-id="4fa96-124">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="4fa96-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4fa96-125">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="4fa96-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="4fa96-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4fa96-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
