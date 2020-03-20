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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175963"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="c28e6-102">IMetaDataAssemblyImport::GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="c28e6-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="c28e6-103">使用指定的中繼資料簽名獲取程式集引用的屬性集。</span><span class="sxs-lookup"><span data-stu-id="c28e6-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c28e6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c28e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="c28e6-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="c28e6-106">[在]表示`mdAssemblyRef`要獲取屬性的程式集引用的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="c28e6-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="c28e6-107">[出]指向公開金鑰或中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="c28e6-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="c28e6-108">[出]返回的公開金鑰或權杖中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="c28e6-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="c28e6-109">[出]程式集的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="c28e6-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c28e6-110">[在]大字元的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="c28e6-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c28e6-111">[出]指向 中實際返回的寬字元數的指標`szName`。</span><span class="sxs-lookup"><span data-stu-id="c28e6-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c28e6-112">[出]指向包含組件中繼資料的裝配元資料結構的指標。</span><span class="sxs-lookup"><span data-stu-id="c28e6-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="c28e6-113">[出]指向雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="c28e6-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="c28e6-114">這是使用 SHA-1 演算法引用的程式集`PublicKey`屬性的雜湊值，除非設置了[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)枚舉的 arfFullOriginator 標誌。</span><span class="sxs-lookup"><span data-stu-id="c28e6-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="c28e6-115">[出]返回的雜湊值中的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="c28e6-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="c28e6-116">[出]指向用於描述應用於程式集的中繼資料的標誌的指標。</span><span class="sxs-lookup"><span data-stu-id="c28e6-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="c28e6-117">標誌值是一個或多個[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="c28e6-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c28e6-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="c28e6-118">Return Value</span></span>  
 <span data-ttu-id="c28e6-119">此方法如果成功，將返回S_OK;否則，它將返回 Winerror.h 標標頭檔中定義的錯誤代碼之一。</span><span class="sxs-lookup"><span data-stu-id="c28e6-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28e6-120">需求</span><span class="sxs-lookup"><span data-stu-id="c28e6-120">Requirements</span></span>  
 <span data-ttu-id="c28e6-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c28e6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28e6-122">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="c28e6-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c28e6-123">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c28e6-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c28e6-124">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28e6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28e6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c28e6-125">See also</span></span>

- [<span data-ttu-id="c28e6-126">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="c28e6-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
