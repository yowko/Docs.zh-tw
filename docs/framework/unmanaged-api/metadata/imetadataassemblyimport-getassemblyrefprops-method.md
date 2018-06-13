---
title: IMetaDataAssemblyImport::GetAssemblyRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0810ba945c1ed5874dae79704362a399c7349604
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445818"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="926f8-102">IMetaDataAssemblyImport::GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="926f8-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="926f8-103">取得與指定的中繼資料簽章的組件參考的屬性集。</span><span class="sxs-lookup"><span data-stu-id="926f8-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="926f8-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="926f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="926f8-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="926f8-106">[in]`mdAssemblyRef`代表要取得屬性的組件參考的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="926f8-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="926f8-107">[out]公開金鑰或中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="926f8-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="926f8-108">[out]在傳回的公開金鑰或語彙基元的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="926f8-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="926f8-109">[out]組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="926f8-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="926f8-110">[in]大小，以寬字元的`szName`。</span><span class="sxs-lookup"><span data-stu-id="926f8-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="926f8-111">[out]中實際傳回的寬字元數目的指標`szName`。</span><span class="sxs-lookup"><span data-stu-id="926f8-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="926f8-112">[out]ASSEMBLYMETADATA 結構，其中包含組件中繼資料指標。</span><span class="sxs-lookup"><span data-stu-id="926f8-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="926f8-113">[out]雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="926f8-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="926f8-114">這是雜湊，並使用 sha-1 演算法的`PublicKey`屬性的參考，除非 arfFullOriginator 旗標之組件[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)列舉集合。</span><span class="sxs-lookup"><span data-stu-id="926f8-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="926f8-115">[out]傳回雜湊值中的寬字元數目。</span><span class="sxs-lookup"><span data-stu-id="926f8-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="926f8-116">[out]旗標，敘述套用至組件的中繼資料指標。</span><span class="sxs-lookup"><span data-stu-id="926f8-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="926f8-117">旗標值是一或多個組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="926f8-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="926f8-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="926f8-118">Return Value</span></span>  
 <span data-ttu-id="926f8-119">這個方法會傳回 S_OK，如果它成功。否則，它會傳回其中 Winerror.h 標頭檔中定義的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="926f8-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="926f8-120">需求</span><span class="sxs-lookup"><span data-stu-id="926f8-120">Requirements</span></span>  
 <span data-ttu-id="926f8-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="926f8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="926f8-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="926f8-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="926f8-123">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="926f8-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="926f8-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="926f8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926f8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="926f8-125">See Also</span></span>  
 [<span data-ttu-id="926f8-126">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="926f8-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
