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
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177651"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="87bee-102">IMetaDataAssemblyImport::GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="87bee-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="87bee-103">使用指定的中繼資料簽名獲取清單資源的屬性集。</span><span class="sxs-lookup"><span data-stu-id="87bee-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87bee-104">語法</span><span class="sxs-lookup"><span data-stu-id="87bee-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="87bee-105">參數</span><span class="sxs-lookup"><span data-stu-id="87bee-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="87bee-106">[在]表示`mdManifestResource`要為其獲取屬性的資源的權杖。</span><span class="sxs-lookup"><span data-stu-id="87bee-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="87bee-107">[出]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="87bee-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="87bee-108">[在]大字元的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="87bee-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="87bee-109">[出]指向 中實際返回的寬字元數的指標`szName`。</span><span class="sxs-lookup"><span data-stu-id="87bee-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="87bee-110">[出]指向分別表示包含`mdFile`資源的檔或`mdAssemblyRef`程式集的權杖或權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="87bee-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="87bee-111">[出]指向指定偏移到檔中資源開頭的值的指標。</span><span class="sxs-lookup"><span data-stu-id="87bee-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="87bee-112">[出]指向用於描述應用於資源的中繼資料的標誌的指標。</span><span class="sxs-lookup"><span data-stu-id="87bee-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="87bee-113">標誌值是一個或多個[CorManifest 資源標誌](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="87bee-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87bee-114">需求</span><span class="sxs-lookup"><span data-stu-id="87bee-114">Requirements</span></span>  
 <span data-ttu-id="87bee-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87bee-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87bee-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="87bee-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87bee-117">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="87bee-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87bee-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87bee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87bee-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87bee-119">See also</span></span>

- [<span data-ttu-id="87bee-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="87bee-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
