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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9babd5e50166be2c2d1b7bc32a5fc11d1ad8ba9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930560"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="b9558-102">IMetaDataAssemblyImport::FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="b9558-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="b9558-103">取得具有指定的組件的陣列`szAssemblyName`參數，用來解析參考的 common language runtime (CLR) 所採用的標準規則。</span><span class="sxs-lookup"><span data-stu-id="b9558-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9558-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9558-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9558-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9558-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="b9558-106">[in]要在其中搜尋指定的組件的根目錄。</span><span class="sxs-lookup"><span data-stu-id="b9558-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="b9558-107">如果此值設為`null`，`FindAssembliesByName`會尋找只在全域組件快取中組件。</span><span class="sxs-lookup"><span data-stu-id="b9558-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="b9558-108">[in]以分號分隔 （例如，「 bin; bin2"） 下, 子目錄的根目錄，在其中搜尋組件清單。</span><span class="sxs-lookup"><span data-stu-id="b9558-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="b9558-109">除了預設探查規則中所指定會探查下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b9558-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="b9558-110">[in]若要尋找組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9558-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="b9558-111">此字串的格式定義的類別參考頁面<xref:System.Reflection.AssemblyName>。</span><span class="sxs-lookup"><span data-stu-id="b9558-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b9558-112">[in]類型的陣列[IUnknown](/cpp/atl/iunknown)要放入`IMetadataAssemblyImport`介面指標。</span><span class="sxs-lookup"><span data-stu-id="b9558-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b9558-113">[out]可以放在的介面指標的最大數目`ppIUnk`。</span><span class="sxs-lookup"><span data-stu-id="b9558-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="b9558-114">[out]傳回的介面指標的數目。</span><span class="sxs-lookup"><span data-stu-id="b9558-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="b9558-115">也就是介面指標的數目實際放在`ppIUnk`。</span><span class="sxs-lookup"><span data-stu-id="b9558-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9558-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9558-116">Return Value</span></span>  
  
|<span data-ttu-id="b9558-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9558-117">HRESULT</span></span>|<span data-ttu-id="b9558-118">描述</span><span class="sxs-lookup"><span data-stu-id="b9558-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9558-119">`FindAssembliesByName` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b9558-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b9558-120">沒有組件。</span><span class="sxs-lookup"><span data-stu-id="b9558-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9558-121">備註</span><span class="sxs-lookup"><span data-stu-id="b9558-121">Remarks</span></span>  
 <span data-ttu-id="b9558-122">授與組件的名稱，`FindAssembliesByName`方法會遵循標準的規則，以便解析組件參考來尋找組件。</span><span class="sxs-lookup"><span data-stu-id="b9558-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="b9558-123">(如需詳細資訊，請參閱 <<c0> [ 執行階段如何找出組件](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)`FindAssembliesByName`允許呼叫端設定的組件解析程式的內容，例如應用程式基底和私用的搜尋路徑的各種層面。</span><span class="sxs-lookup"><span data-stu-id="b9558-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="b9558-124">`FindAssembliesByName`方法需要 CLR 初始化程序中，才能叫用組件解析邏輯。</span><span class="sxs-lookup"><span data-stu-id="b9558-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="b9558-125">因此，您必須呼叫[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) （傳遞 COINITEE_DEFAULT） 然後再呼叫`FindAssembliesByName`，然後依照呼叫[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)。</span><span class="sxs-lookup"><span data-stu-id="b9558-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="b9558-126">`FindAssembliesByName` 會傳回[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)傳入的檔案包含組件名稱的組件資訊清單的指標。</span><span class="sxs-lookup"><span data-stu-id="b9558-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="b9558-127">如果指定的組件名稱完全未指定 （例如，如果它不包含版本），可能會傳回多個組件。</span><span class="sxs-lookup"><span data-stu-id="b9558-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="b9558-128">`FindAssembliesByName` 通常會使用嘗試尋找參考的組件在編譯時期的編譯器。</span><span class="sxs-lookup"><span data-stu-id="b9558-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9558-129">需求</span><span class="sxs-lookup"><span data-stu-id="b9558-129">Requirements</span></span>  
 <span data-ttu-id="b9558-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9558-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9558-131">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9558-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9558-132">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b9558-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9558-133">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9558-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9558-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9558-134">See Also</span></span>  
 [<span data-ttu-id="b9558-135">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="b9558-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="b9558-136">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="b9558-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
