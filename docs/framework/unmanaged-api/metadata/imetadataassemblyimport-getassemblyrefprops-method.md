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
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="e7805-102">IMetaDataAssemblyImport::GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="e7805-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="e7805-103">取得具有指定的中繼資料簽章之元件參考的屬性集。</span><span class="sxs-lookup"><span data-stu-id="e7805-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7805-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7805-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e7805-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7805-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="e7805-106">在`mdAssemblyRef` 元資料標記，代表要取得其屬性的元件參考。</span><span class="sxs-lookup"><span data-stu-id="e7805-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="e7805-107">脫銷公用金鑰或元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="e7805-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="e7805-108">脫銷傳回的公開金鑰或 token 中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="e7805-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="e7805-109">脫銷元件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="e7805-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e7805-110">在`szName`的大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="e7805-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e7805-111">脫銷`szName`中實際傳回的寬字元數指標。</span><span class="sxs-lookup"><span data-stu-id="e7805-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="e7805-112">脫銷包含元件中繼資料之 ASSEMBLYMETADATA 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="e7805-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="e7805-113">脫銷雜湊值的指標。</span><span class="sxs-lookup"><span data-stu-id="e7805-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="e7805-114">這是要參考之元件的 `PublicKey` 屬性的雜湊（使用 SHA-1 演算法），除非已設定[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)列舉的 arfFullOriginator 旗標。</span><span class="sxs-lookup"><span data-stu-id="e7805-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="e7805-115">脫銷傳回的雜湊值中的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="e7805-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="e7805-116">脫銷旗標的指標，描述套用至元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e7805-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="e7805-117">旗標值是一個或多個[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="e7805-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7805-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="e7805-118">Return Value</span></span>  
 <span data-ttu-id="e7805-119">如果成功，這個方法會傳回 S_OK;否則，它會傳回 Winerror.h 標頭檔中所定義的其中一個錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e7805-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7805-120">需求</span><span class="sxs-lookup"><span data-stu-id="e7805-120">Requirements</span></span>  
 <span data-ttu-id="e7805-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7805-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7805-122">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e7805-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7805-123">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e7805-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7805-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7805-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7805-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7805-125">See also</span></span>

- [<span data-ttu-id="e7805-126">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="e7805-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
