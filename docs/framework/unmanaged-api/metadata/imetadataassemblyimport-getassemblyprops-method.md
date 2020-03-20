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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177793"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="b6f22-102">IMetaDataAssemblyImport::GetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="b6f22-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="b6f22-103">使用指定的中繼資料簽名獲取程式集的屬性集。</span><span class="sxs-lookup"><span data-stu-id="b6f22-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f22-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6f22-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="b6f22-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6f22-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="b6f22-106">[在]。</span><span class="sxs-lookup"><span data-stu-id="b6f22-106">[in].</span></span> <span data-ttu-id="b6f22-107">表示`mdAssembly`要為其獲取屬性的程式集的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="b6f22-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="b6f22-108">[出]指向公開金鑰或中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="b6f22-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b6f22-109">[出]返回的公開金鑰中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="b6f22-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="b6f22-110">[出]指向用於雜湊程式集中檔的演算法的指標。</span><span class="sxs-lookup"><span data-stu-id="b6f22-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="b6f22-111">[出]程式集的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f22-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b6f22-112">[在]大字元的大小`szName`。</span><span class="sxs-lookup"><span data-stu-id="b6f22-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b6f22-113">[出]中實際返回的寬字元數`szName`。</span><span class="sxs-lookup"><span data-stu-id="b6f22-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="b6f22-114">[出]指向包含組件中繼資料的裝配元資料結構的指標。</span><span class="sxs-lookup"><span data-stu-id="b6f22-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="b6f22-115">[出]描述應用於程式集的中繼資料的標誌。</span><span class="sxs-lookup"><span data-stu-id="b6f22-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="b6f22-116">此值是一個或多個[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="b6f22-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6f22-117">需求</span><span class="sxs-lookup"><span data-stu-id="b6f22-117">Requirements</span></span>  
 <span data-ttu-id="b6f22-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f22-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f22-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="b6f22-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6f22-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6f22-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6f22-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f22-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f22-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6f22-122">See also</span></span>

- [<span data-ttu-id="b6f22-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="b6f22-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
