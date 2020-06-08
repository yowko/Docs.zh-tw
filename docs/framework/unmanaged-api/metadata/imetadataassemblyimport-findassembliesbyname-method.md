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
ms.openlocfilehash: d2693a94f02214df6d7265b26e3d70d91adcf8a7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503831"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="6dd99-102">IMetaDataAssemblyImport::FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="6dd99-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="6dd99-103">`szAssemblyName`使用 common language runtime （CLR）用來解析參考的標準規則，取得具有指定參數的元件陣列。</span><span class="sxs-lookup"><span data-stu-id="6dd99-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd99-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dd99-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6dd99-105">參數</span><span class="sxs-lookup"><span data-stu-id="6dd99-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="6dd99-106">在要在其中搜尋指定元件的根目錄。</span><span class="sxs-lookup"><span data-stu-id="6dd99-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="6dd99-107">如果這個值設定為 `null` ， `FindAssembliesByName` 則只會查看元件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="6dd99-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="6dd99-108">在根目錄底下以分號分隔的子目錄清單（例如，"bin; bin2"），在該目錄中會搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="6dd99-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="6dd99-109">除了預設探查規則中指定的目錄以外，還會探查這些目錄。</span><span class="sxs-lookup"><span data-stu-id="6dd99-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="6dd99-110">在要尋找之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dd99-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="6dd99-111">這個字串的格式定義于的 [類別參考] 頁面中 <xref:System.Reflection.AssemblyName> 。</span><span class="sxs-lookup"><span data-stu-id="6dd99-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6dd99-112">在[IUnknown](/cpp/atl/iunknown)類型的陣列，要在其中放置 `IMetadataAssemblyImport` 介面指標。</span><span class="sxs-lookup"><span data-stu-id="6dd99-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6dd99-113">脫銷可以放入的介面指標的最大數目 `ppIUnk` 。</span><span class="sxs-lookup"><span data-stu-id="6dd99-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="6dd99-114">脫銷傳回的介面指標數目。</span><span class="sxs-lookup"><span data-stu-id="6dd99-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="6dd99-115">也就是，實際放入的介面指標數目 `ppIUnk` 。</span><span class="sxs-lookup"><span data-stu-id="6dd99-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dd99-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dd99-116">Return Value</span></span>  
  
|<span data-ttu-id="6dd99-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6dd99-117">HRESULT</span></span>|<span data-ttu-id="6dd99-118">說明</span><span class="sxs-lookup"><span data-stu-id="6dd99-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6dd99-119">`FindAssembliesByName`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6dd99-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6dd99-120">沒有任何元件。</span><span class="sxs-lookup"><span data-stu-id="6dd99-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dd99-121">備註</span><span class="sxs-lookup"><span data-stu-id="6dd99-121">Remarks</span></span>  
 <span data-ttu-id="6dd99-122">在指定元件名稱的 `FindAssembliesByName` 情況下，方法會依照解析元件參考的標準規則來尋找元件。</span><span class="sxs-lookup"><span data-stu-id="6dd99-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="6dd99-123">（如需詳細資訊，請參閱[執行時間如何找出元件](../../deployment/how-the-runtime-locates-assemblies.md)）。`FindAssembliesByName`可讓呼叫者設定元件解析程式內容的各種層面，例如應用程式基底和私用搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="6dd99-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="6dd99-124">方法需要在進程中初始化 CLR，才能叫用 `FindAssembliesByName` 元件解析邏輯。</span><span class="sxs-lookup"><span data-stu-id="6dd99-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="6dd99-125">因此，在呼叫之前，您必須呼叫[CoInitializeEE](../hosting/coinitializeee-function.md) （傳遞 COINITEE_DEFAULT）， `FindAssembliesByName` 然後遵循[CoUninitializeCor](../hosting/couninitializecor-function.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="6dd99-125">Therefore, you must call [CoInitializeEE](../hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="6dd99-126">`FindAssembliesByName`傳回檔案的[IMetaDataImport](imetadataimport-interface.md)指標，此檔案包含傳入之元件名稱的組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="6dd99-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="6dd99-127">如果未完整指定給定的元件名稱（例如，如果它不包含版本），則可能會傳回多個元件。</span><span class="sxs-lookup"><span data-stu-id="6dd99-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="6dd99-128">`FindAssembliesByName`編譯器常用於嘗試在編譯時期尋找參考元件的編譯器。</span><span class="sxs-lookup"><span data-stu-id="6dd99-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd99-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="6dd99-129">Requirements</span></span>  
 <span data-ttu-id="6dd99-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd99-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dd99-131">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6dd99-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6dd99-132">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6dd99-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6dd99-133">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd99-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd99-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd99-134">See also</span></span>

- [<span data-ttu-id="6dd99-135">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="6dd99-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6dd99-136">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="6dd99-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
