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
ms.openlocfilehash: 911d0d1444e2cf3cb8241eeeff63a5a86b4ab806
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446270"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="88099-102">IMetaDataAssemblyImport::GetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="88099-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="88099-103">取得具有指定的中繼資料簽章的組件的屬性集。</span><span class="sxs-lookup"><span data-stu-id="88099-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88099-104">語法</span><span class="sxs-lookup"><span data-stu-id="88099-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="88099-105">參數</span><span class="sxs-lookup"><span data-stu-id="88099-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="88099-106">[in]。</span><span class="sxs-lookup"><span data-stu-id="88099-106">[in].</span></span> <span data-ttu-id="88099-107">`mdAssembly`代表要取得屬性的組件的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="88099-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="88099-108">[out]公開金鑰或中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="88099-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="88099-109">[out]在傳回的公開金鑰的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="88099-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="88099-110">[out]指標，用來雜湊中的組件檔案的演算法。</span><span class="sxs-lookup"><span data-stu-id="88099-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="88099-111">[out]組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="88099-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="88099-112">[in]大小，以寬字元的`szName`。</span><span class="sxs-lookup"><span data-stu-id="88099-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="88099-113">[out]中實際傳回的寬字元數目`szName`。</span><span class="sxs-lookup"><span data-stu-id="88099-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="88099-114">[out]ASSEMBLYMETADATA 結構，其中包含組件中繼資料指標。</span><span class="sxs-lookup"><span data-stu-id="88099-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="88099-115">[out]描述套用至組件的中繼資料的旗標。</span><span class="sxs-lookup"><span data-stu-id="88099-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="88099-116">這個值是一或多個組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="88099-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88099-117">需求</span><span class="sxs-lookup"><span data-stu-id="88099-117">Requirements</span></span>  
 <span data-ttu-id="88099-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88099-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88099-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="88099-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88099-120">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="88099-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88099-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88099-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88099-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88099-122">See Also</span></span>  
 [<span data-ttu-id="88099-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="88099-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
