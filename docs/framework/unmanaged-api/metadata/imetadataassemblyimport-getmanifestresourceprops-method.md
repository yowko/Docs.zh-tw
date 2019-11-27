---
title: IMetaDataAssemblyImport::GetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: c1792ed0f15f8cfb62567593c9694453650f0bb9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436325"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="83e32-102">IMetaDataAssemblyImport::GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="83e32-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="83e32-103">取得具有指定之中繼資料簽章之資訊清單資源的屬性集。</span><span class="sxs-lookup"><span data-stu-id="83e32-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e32-104">語法</span><span class="sxs-lookup"><span data-stu-id="83e32-104">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e32-105">參數</span><span class="sxs-lookup"><span data-stu-id="83e32-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="83e32-106">在`mdManifestResource` token，代表要取得其屬性的資源。</span><span class="sxs-lookup"><span data-stu-id="83e32-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="83e32-107">脫銷資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="83e32-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="83e32-108">在`szName`的大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="83e32-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="83e32-109">脫銷`szName`中實際傳回的寬字元數指標。</span><span class="sxs-lookup"><span data-stu-id="83e32-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="83e32-110">脫銷`mdFile` token 或 `mdAssemblyRef` token 的指標，分別代表包含資源的檔案或元件。</span><span class="sxs-lookup"><span data-stu-id="83e32-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="83e32-111">脫銷值的指標，指定檔案內資源開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="83e32-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="83e32-112">脫銷旗標的指標，描述套用至資源的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="83e32-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="83e32-113">旗標值是一個或多個[CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="83e32-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e32-114">需求</span><span class="sxs-lookup"><span data-stu-id="83e32-114">Requirements</span></span>  
 <span data-ttu-id="83e32-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83e32-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e32-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="83e32-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83e32-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="83e32-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83e32-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e32-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e32-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="83e32-119">See also</span></span>

- [<span data-ttu-id="83e32-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="83e32-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
