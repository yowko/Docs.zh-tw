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
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009024"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="1bab4-102">IMetaDataAssemblyImport::GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="1bab4-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="1bab4-103">取得具有指定之中繼資料簽章之資訊清單資源的屬性集。</span><span class="sxs-lookup"><span data-stu-id="1bab4-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bab4-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bab4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1bab4-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bab4-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="1bab4-106">在`mdManifestResource`Token，代表要取得其屬性的資源。</span><span class="sxs-lookup"><span data-stu-id="1bab4-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="1bab4-107">脫銷資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bab4-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1bab4-108">在的大小（以寬字元為單位） `szName` 。</span><span class="sxs-lookup"><span data-stu-id="1bab4-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1bab4-109">脫銷中實際傳回的寬字元數指標 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="1bab4-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="1bab4-110">脫銷`mdFile`標記或 `mdAssemblyRef` token 的指標，分別代表包含資源的檔案或元件。</span><span class="sxs-lookup"><span data-stu-id="1bab4-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="1bab4-111">脫銷值的指標，指定檔案內資源開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="1bab4-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="1bab4-112">脫銷旗標的指標，描述套用至資源的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1bab4-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="1bab4-113">旗標值是一個或多個[CorManifestResourceFlags](cormanifestresourceflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="1bab4-113">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bab4-114">需求</span><span class="sxs-lookup"><span data-stu-id="1bab4-114">Requirements</span></span>  
 <span data-ttu-id="1bab4-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bab4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bab4-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1bab4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1bab4-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1bab4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1bab4-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bab4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bab4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bab4-119">See also</span></span>

- [<span data-ttu-id="1bab4-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="1bab4-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
