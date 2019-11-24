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
ms.openlocfilehash: 4149db74adfa26df221eed5c590766a023bb105e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448233"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="03310-102">IMetaDataAssemblyImport::GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="03310-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="03310-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span><span class="sxs-lookup"><span data-stu-id="03310-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03310-104">語法</span><span class="sxs-lookup"><span data-stu-id="03310-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="03310-105">參數</span><span class="sxs-lookup"><span data-stu-id="03310-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="03310-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span><span class="sxs-lookup"><span data-stu-id="03310-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="03310-107">[out] A pointer to the public key or the metadata token.</span><span class="sxs-lookup"><span data-stu-id="03310-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="03310-108">[out] The number of bytes in the returned public key or token.</span><span class="sxs-lookup"><span data-stu-id="03310-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="03310-109">[out] The simple name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="03310-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="03310-110">[in] The size, in wide chars, of `szName`.</span><span class="sxs-lookup"><span data-stu-id="03310-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="03310-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="03310-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="03310-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span><span class="sxs-lookup"><span data-stu-id="03310-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="03310-113">[out] A pointer to the hash value.</span><span class="sxs-lookup"><span data-stu-id="03310-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="03310-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span><span class="sxs-lookup"><span data-stu-id="03310-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="03310-115">[out] The number of wide chars in the returned hash value.</span><span class="sxs-lookup"><span data-stu-id="03310-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="03310-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span><span class="sxs-lookup"><span data-stu-id="03310-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="03310-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span><span class="sxs-lookup"><span data-stu-id="03310-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03310-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="03310-118">Return Value</span></span>  
 <span data-ttu-id="03310-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span><span class="sxs-lookup"><span data-stu-id="03310-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03310-120">需求</span><span class="sxs-lookup"><span data-stu-id="03310-120">Requirements</span></span>  
 <span data-ttu-id="03310-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03310-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03310-122">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03310-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03310-123">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03310-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03310-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03310-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03310-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="03310-125">See also</span></span>

- [<span data-ttu-id="03310-126">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="03310-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
