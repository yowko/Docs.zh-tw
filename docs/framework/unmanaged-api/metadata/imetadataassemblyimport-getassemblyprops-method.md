---
title: IMetaDataAssemblyImport::GetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4817a62d276bfdb50bfcbf658f40f5568673bea0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163211"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="65c91-102">IMetaDataAssemblyImport::GetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="65c91-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="65c91-103">取得具有指定之中繼資料簽章的組件的屬性集。</span><span class="sxs-lookup"><span data-stu-id="65c91-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c91-104">語法</span><span class="sxs-lookup"><span data-stu-id="65c91-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c91-105">參數</span><span class="sxs-lookup"><span data-stu-id="65c91-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="65c91-106">[in].</span><span class="sxs-lookup"><span data-stu-id="65c91-106">[in].</span></span> <span data-ttu-id="65c91-107">`mdAssembly`表示要為其取得屬性的組件的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="65c91-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="65c91-108">[out]公開金鑰或中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="65c91-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="65c91-109">[out]在傳回的公開金鑰的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="65c91-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="65c91-110">[out]指標，用來雜湊組件中的檔案的演算法。</span><span class="sxs-lookup"><span data-stu-id="65c91-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="65c91-111">[out]組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="65c91-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="65c91-112">[in]大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="65c91-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="65c91-113">[out]中實際傳回的寬字元數目`szName`。</span><span class="sxs-lookup"><span data-stu-id="65c91-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="65c91-114">[out]ASSEMBLYMETADATA 結構，其中包含組件中繼資料指標。</span><span class="sxs-lookup"><span data-stu-id="65c91-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="65c91-115">[out]描述套用至組件的中繼資料的旗標。</span><span class="sxs-lookup"><span data-stu-id="65c91-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="65c91-116">這個值是由一或多個組成[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="65c91-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c91-117">需求</span><span class="sxs-lookup"><span data-stu-id="65c91-117">Requirements</span></span>  
 <span data-ttu-id="65c91-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65c91-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c91-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65c91-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65c91-120">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="65c91-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="65c91-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="65c91-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65c91-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65c91-122">See also</span></span>

- [<span data-ttu-id="65c91-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="65c91-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
