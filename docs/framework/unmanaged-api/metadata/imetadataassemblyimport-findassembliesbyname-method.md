---
title: IMetaDataAssemblyImport::FindAssembliesByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177806"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="bb3fd-102">IMetaDataAssemblyImport::FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="bb3fd-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="bb3fd-103">使用通用語言運行時 （CLR） 採用的標準規則解析引用，獲取具有指定`szAssemblyName`參數的程式集陣列。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb3fd-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb3fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb3fd-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="bb3fd-106">[在]要在其中搜索給定程式集的根目錄。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="bb3fd-107">如果此值設置為`null`，`FindAssembliesByName`將僅在程式集的全域組件快取中查找。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="bb3fd-108">[在]在根目錄下搜索程式集的分號分隔子目錄（例如，"bin;bin2"）的清單。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="bb3fd-109">除了預設探測規則中指定的目錄外，這些目錄還被探測。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="bb3fd-110">[在]要查找的程式集的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="bb3fd-111">此字串的格式在 的類引用頁中<xref:System.Reflection.AssemblyName>定義。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="bb3fd-112">[在]放置`IMetadataAssemblyImport`介面指標的[I 未知](/cpp/atl/iunknown)類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bb3fd-113">[出]可放置在 中的最大介面指標數`ppIUnk`。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="bb3fd-114">[出]返回的介面指標數。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="bb3fd-115">也就是說，實際上放置在 中的`ppIUnk`介面指標數。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb3fd-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="bb3fd-116">Return Value</span></span>  
  
|<span data-ttu-id="bb3fd-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb3fd-117">HRESULT</span></span>|<span data-ttu-id="bb3fd-118">描述</span><span class="sxs-lookup"><span data-stu-id="bb3fd-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bb3fd-119">`FindAssembliesByName`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bb3fd-120">沒有程式集。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb3fd-121">備註</span><span class="sxs-lookup"><span data-stu-id="bb3fd-121">Remarks</span></span>  
 <span data-ttu-id="bb3fd-122">給定程式集名稱，`FindAssembliesByName`該方法通過遵循解析程式集引用的標準規則來查找程式集。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="bb3fd-123">（有關詳細資訊，請參閱[運行時如何查找程式集](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。`FindAssembliesByName`允許調用方配置程式集解析器上下文的各個方面，如應用程式庫和專用搜索路徑。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="bb3fd-124">該方法`FindAssembliesByName`要求在進程中初始化 CLR，以便調用程式集解析邏輯。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="bb3fd-125">因此，在調用`FindAssembliesByName`之前必須調用[Co初始化EEE（](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)傳遞COINITEE_DEFAULT），然後調用[CoUn初始化Cor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="bb3fd-126">`FindAssembliesByName`返回[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)指標，指向包含傳入的程式集名稱的組件資訊清單的檔。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="bb3fd-127">如果未完全指定給定程式集名稱（例如，如果不包括版本），則可能會返回多個程式集。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="bb3fd-128">`FindAssembliesByName`嘗試在編譯時查找引用程式集的編譯器通常使用。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3fd-129">需求</span><span class="sxs-lookup"><span data-stu-id="bb3fd-129">Requirements</span></span>  
 <span data-ttu-id="bb3fd-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb3fd-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3fd-131">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="bb3fd-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb3fd-132">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bb3fd-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb3fd-133">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3fd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3fd-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb3fd-134">See also</span></span>

- [<span data-ttu-id="bb3fd-135">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="bb3fd-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="bb3fd-136">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="bb3fd-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
