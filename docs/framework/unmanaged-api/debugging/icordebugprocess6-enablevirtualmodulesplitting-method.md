---
title: ICorDebugProcess6::EnableVirtualModuleSplitting 方法
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bd06dd3f58a1f74fbdb5ec61c4896f5c1696856
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931063"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="b25d6-102">ICorDebugProcess6::EnableVirtualModuleSplitting 方法</span><span class="sxs-lookup"><span data-stu-id="b25d6-102">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>
<span data-ttu-id="b25d6-103">啟用或停用虛擬模組分割。</span><span class="sxs-lookup"><span data-stu-id="b25d6-103">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="b25d6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b25d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="b25d6-105">Parameters</span></span>  
 `enableSplitting`  
 <span data-ttu-id="b25d6-106">若要啟用虛擬模組分割，則為 `true`；若要停用，則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b25d6-106">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b25d6-107">備註</span><span class="sxs-lookup"><span data-stu-id="b25d6-107">Remarks</span></span>  
 <span data-ttu-id="b25d6-108">虛擬模組分割可讓[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)辨識在組建程式期間合併在一起的模組, 並將其呈現為一組不同的模組, 而不是單一的大型模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-108">Virtual module splitting causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="b25d6-109">這麼做會變更各種[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法的行為, 如下所述。</span><span class="sxs-lookup"><span data-stu-id="b25d6-109">Doing this changes the behavior of various [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b25d6-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="b25d6-110">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="b25d6-111">您可以呼叫這個方法並隨時變更 `enableSplitting` 的值。</span><span class="sxs-lookup"><span data-stu-id="b25d6-111">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="b25d6-112">除了改變[虛擬模組分割和未受管理的調試](#APIs)程式開發介面一節中所列的方法行為之外, 它不會在[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件中造成任何具狀態的功能變更。</span><span class="sxs-lookup"><span data-stu-id="b25d6-112">It does not cause any stateful functional changes in an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="b25d6-113">呼叫這些方法時，使用虛擬模組確實會對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="b25d6-113">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="b25d6-114">此外, 可能需要虛擬化中繼資料的大量記憶體內部快取, 才能正確地執行[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) api, 而且即使在關閉虛擬模組分割之後, 這些快取也可能會保留。</span><span class="sxs-lookup"><span data-stu-id="b25d6-114">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="b25d6-115">用語</span><span class="sxs-lookup"><span data-stu-id="b25d6-115">Terminology</span></span>  
 <span data-ttu-id="b25d6-116">描述虛擬模組分割時會使用下列詞彙：</span><span class="sxs-lookup"><span data-stu-id="b25d6-116">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="b25d6-117">容器模組或容器</span><span class="sxs-lookup"><span data-stu-id="b25d6-117">container modules, or containers</span></span>  
 <span data-ttu-id="b25d6-118">彙總模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-118">The aggregate modules.</span></span>  
  
 <span data-ttu-id="b25d6-119">子模組或虛擬模組</span><span class="sxs-lookup"><span data-stu-id="b25d6-119">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="b25d6-120">在容器中找到的模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-120">The modules found in a container.</span></span>  
  
 <span data-ttu-id="b25d6-121">一般模組</span><span class="sxs-lookup"><span data-stu-id="b25d6-121">regular modules</span></span>  
 <span data-ttu-id="b25d6-122">建置時間未合併的模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-122">Modules that were not merged at build time.</span></span> <span data-ttu-id="b25d6-123">這些模組不是容器模組，就是子模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-123">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="b25d6-124">容器模組和子模組都會以 ICorDebugModule 介面物件來表示。</span><span class="sxs-lookup"><span data-stu-id="b25d6-124">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="b25d6-125">不過, 在每個案例中, 介面的行為會稍有不同, \<因為 > 一節中的 x 參考一節所述。</span><span class="sxs-lookup"><span data-stu-id="b25d6-125">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="b25d6-126">模組和組件</span><span class="sxs-lookup"><span data-stu-id="b25d6-126">Modules and assemblies</span></span>  
 <span data-ttu-id="b25d6-127">組件合併案例不支援多模組組件，因此模組和組件之間有一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="b25d6-127">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="b25d6-128">無論每個 ICorDebugModule 物件是否代表容器模組或子模組, 都有對應的 ICorDebugAssembly 物件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-128">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="b25d6-129">[ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法會將模組轉換成元件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-129">The [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="b25d6-130">為了在另一個方向進行對應, [ICorDebugAssembly:: EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)方法只會列舉1個模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-130">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="b25d6-131">由於組件和模組在此情況下會形成緊密結合的配對，因此組件和模組兩個詞彙的互換情況會更高。</span><span class="sxs-lookup"><span data-stu-id="b25d6-131">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="b25d6-132">行為的差異</span><span class="sxs-lookup"><span data-stu-id="b25d6-132">Behavioral differences</span></span>  
 <span data-ttu-id="b25d6-133">容器模組具有下列行為和特性：</span><span class="sxs-lookup"><span data-stu-id="b25d6-133">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="b25d6-134">所有構成子模組的中繼資料會合併在一起。</span><span class="sxs-lookup"><span data-stu-id="b25d6-134">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="b25d6-135">其類型名稱可能會受損。</span><span class="sxs-lookup"><span data-stu-id="b25d6-135">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="b25d6-136">[ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法會傳回磁片上模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="b25d6-136">The [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="b25d6-137">[ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法會傳回該影像的大小。</span><span class="sxs-lookup"><span data-stu-id="b25d6-137">The [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="b25d6-138">ICorDebugAssembly3.EnumerateContainedAssemblies 方法會列出子模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-138">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="b25d6-139">ICorDebugAssembly3.GetContainerAssembly 方法會傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="b25d6-139">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="b25d6-140">子模組具有下列行為和特性：</span><span class="sxs-lookup"><span data-stu-id="b25d6-140">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="b25d6-141">子模組包含一組縮減的中繼資料，只對應至已合併的原始組件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-141">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="b25d6-142">中繼資料名稱不會受損。</span><span class="sxs-lookup"><span data-stu-id="b25d6-142">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="b25d6-143">中繼資料語彙基元不太可能符合原始組件在建置流程中合併前的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b25d6-143">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="b25d6-144">[ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法會傳回元件名稱, 而不是檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="b25d6-144">The [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="b25d6-145">[ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法會傳回原始未合併的映射大小。</span><span class="sxs-lookup"><span data-stu-id="b25d6-145">The [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="b25d6-146">ICorDebugModule3.EnumerateContainedAssemblies 方法會傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="b25d6-146">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="b25d6-147">ICorDebugAssembly3.GetContainerAssembly 方法會傳回所包含的模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-147">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="b25d6-148">從模組擷取的介面</span><span class="sxs-lookup"><span data-stu-id="b25d6-148">Interfaces retrieved from modules</span></span>  
 <span data-ttu-id="b25d6-149">可從模組建立或擷取的各種介面。</span><span class="sxs-lookup"><span data-stu-id="b25d6-149">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="b25d6-150">其中包括：</span><span class="sxs-lookup"><span data-stu-id="b25d6-150">Some of these include:</span></span>  
  
- <span data-ttu-id="b25d6-151">[ICorDebugModule:: GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)方法傳回的 ICorDebugClass 物件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-151">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="b25d6-152">[ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法傳回的 ICorDebugAssembly 物件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-152">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="b25d6-153">這些物件一律會由[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)快取, 而且不論是從容器模組或子模組建立或查詢, 它們都會有相同的指標識別。</span><span class="sxs-lookup"><span data-stu-id="b25d6-153">These objects are always cached by [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="b25d6-154">子模組提供這些快取物件的篩選檢視，而不是其本身複本的個別快取。</span><span class="sxs-lookup"><span data-stu-id="b25d6-154">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="b25d6-155">虛擬模組分割和未受管理的偵錯 API</span><span class="sxs-lookup"><span data-stu-id="b25d6-155">Virtual module splitting and the unmanaged debugging APIs</span></span>  
 <span data-ttu-id="b25d6-156">下表顯示虛擬模組分割如何影響未受管理之偵錯 API 中其他方法的行為。</span><span class="sxs-lookup"><span data-stu-id="b25d6-156">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="b25d6-157">方法</span><span class="sxs-lookup"><span data-stu-id="b25d6-157">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="b25d6-158">ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="b25d6-158">ICorDebugFunction::GetModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="b25d6-159">傳回這個函式原本定義所在的子模組</span><span class="sxs-lookup"><span data-stu-id="b25d6-159">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="b25d6-160">傳回已合併這個函式的目標容器模組</span><span class="sxs-lookup"><span data-stu-id="b25d6-160">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="b25d6-161">ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="b25d6-161">ICorDebugClass::GetModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="b25d6-162">傳回這個類別原本定義所在的子模組</span><span class="sxs-lookup"><span data-stu-id="b25d6-162">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="b25d6-163">傳回已合併這個類別的目標容器模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-163">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="b25d6-164">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="b25d6-164">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="b25d6-165">傳回已載入的容器模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-165">Returns the container module that was loaded.</span></span> <span data-ttu-id="b25d6-166">不論這個設定為何，都不會提供載入事件給子模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-166">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="b25d6-167">傳回已載入的容器模組。</span><span class="sxs-lookup"><span data-stu-id="b25d6-167">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="b25d6-168">ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="b25d6-168">ICorDebugAppDomain::EnumerateAssemblies</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="b25d6-169">傳回子組件和一般組件的清單，不包含任何容器組件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-169">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="b25d6-170">**注意：** 如有任何容器組件遺漏符號，則不會列舉其子組件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-170">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="b25d6-171">如有任何一般組件遺漏符號，則列舉或不列舉都有可能。</span><span class="sxs-lookup"><span data-stu-id="b25d6-171">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="b25d6-172">傳回容器組件和一般組件的清單，不包含任何子組件。</span><span class="sxs-lookup"><span data-stu-id="b25d6-172">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="b25d6-173">**注意：** 如有任何一般組件遺漏符號，則列舉或不列舉都有可能。</span><span class="sxs-lookup"><span data-stu-id="b25d6-173">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="b25d6-174">[ICorDebugCode:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)(僅參考 IL 程式碼時)</span><span class="sxs-lookup"><span data-stu-id="b25d6-174">[ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="b25d6-175">傳回在預先合併組件映像中有效的 IL。</span><span class="sxs-lookup"><span data-stu-id="b25d6-175">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="b25d6-176">具體來說，當所參考的類型未在包含 IL 的虛擬模組中定義時，所有內嵌中繼資料語彙基元都會是正確的 TypeRef 或 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b25d6-176">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="b25d6-177">您可以在[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件中, 針對對應的虛擬 ICorDebugModule 物件查閱這些 TypeRef 或 MemberRef 標記。</span><span class="sxs-lookup"><span data-stu-id="b25d6-177">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="b25d6-178">傳回合併後組件映像中的 IL。</span><span class="sxs-lookup"><span data-stu-id="b25d6-178">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b25d6-179">需求</span><span class="sxs-lookup"><span data-stu-id="b25d6-179">Requirements</span></span>  
 <span data-ttu-id="b25d6-180">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b25d6-180">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25d6-181">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b25d6-181">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b25d6-182">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b25d6-182">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b25d6-183">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25d6-183">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25d6-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b25d6-184">See also</span></span>

- [<span data-ttu-id="b25d6-185">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="b25d6-185">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="b25d6-186">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b25d6-186">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
