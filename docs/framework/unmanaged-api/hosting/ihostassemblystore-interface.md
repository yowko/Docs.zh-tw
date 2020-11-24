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
ms.openlocfilehash: 4b2fed963d2d0ebec54e5f7a4d95cba26c1bac1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680934"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="b9caf-102">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="b9caf-102">IHostAssemblyStore Interface</span></span>

<span data-ttu-id="b9caf-103">提供可讓主機獨立載入元件和模組的方法， (CLR) 的通用語言執行時間。</span><span class="sxs-lookup"><span data-stu-id="b9caf-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9caf-104">方法</span><span class="sxs-lookup"><span data-stu-id="b9caf-104">Methods</span></span>  
  
|<span data-ttu-id="b9caf-105">方法</span><span class="sxs-lookup"><span data-stu-id="b9caf-105">Method</span></span>|<span data-ttu-id="b9caf-106">描述</span><span class="sxs-lookup"><span data-stu-id="b9caf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9caf-107">ProvideAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="b9caf-107">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="b9caf-108">取得元件的參考，該元件不是由呼叫[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)所傳回的[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)所參考。</span><span class="sxs-lookup"><span data-stu-id="b9caf-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="b9caf-109">ProvideModule 方法</span><span class="sxs-lookup"><span data-stu-id="b9caf-109">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="b9caf-110">解析元件內的模組，或未內嵌) 資源檔的連結 (。</span><span class="sxs-lookup"><span data-stu-id="b9caf-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9caf-111">備註</span><span class="sxs-lookup"><span data-stu-id="b9caf-111">Remarks</span></span>  

 <span data-ttu-id="b9caf-112">`IHostAssemblyStore` 提供一種方式，讓主機根據元件身分識別有效率地載入元件。</span><span class="sxs-lookup"><span data-stu-id="b9caf-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="b9caf-113">主機會藉由傳回 `IStream` 直接指向位元組的實例來載入元件。</span><span class="sxs-lookup"><span data-stu-id="b9caf-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="b9caf-114">CLR 會透過在 `IHostAssemblyStore` 初始化時呼叫來判斷主機是否已執行 `IHostAssemblyManager::GetNonHostAssemblyStores` 。</span><span class="sxs-lookup"><span data-stu-id="b9caf-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="b9caf-115">例如，這可讓主機控制使用者元件的系結，但是依賴執行時間系結至 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="b9caf-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9caf-116">在提供的執行中 `IHostAssemblyStore` ，主機會指定其意圖，以解析從傳回之所參考的所有元件 `ICLRAssemblyReferenceList` `IHostAssemblyManager::GetNonHostStoreAssemblies` 。</span><span class="sxs-lookup"><span data-stu-id="b9caf-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9caf-117">.NET Framework 版本2.0 未提供方法讓主機載入元件的原生映射，如 [原生映射產生器 ( # A0) ](../../tools/ngen-exe-native-image-generator.md) 公用程式所提供。</span><span class="sxs-lookup"><span data-stu-id="b9caf-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9caf-118">需求</span><span class="sxs-lookup"><span data-stu-id="b9caf-118">Requirements</span></span>  

 <span data-ttu-id="b9caf-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9caf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9caf-120">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b9caf-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9caf-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b9caf-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9caf-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9caf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9caf-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9caf-123">See also</span></span>

- [<span data-ttu-id="b9caf-124">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b9caf-124">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b9caf-125">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b9caf-125">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="b9caf-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b9caf-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
