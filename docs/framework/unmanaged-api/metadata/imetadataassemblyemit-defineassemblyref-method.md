---
title: IMetaDataAssemblyEmit::DefineAssemblyRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c150f4bda901627fc21ed54926c3cf959bb829a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776299"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="5593d-102">IMetaDataAssemblyEmit::DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="5593d-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="5593d-103">為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5593d-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5593d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5593d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5593d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5593d-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="5593d-106">[in]參考的組件的 「 發行者 」 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="5593d-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="5593d-107">Helper 函式[StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)可用來取得的公用金鑰來作為此參數傳遞的雜湊。</span><span class="sxs-lookup"><span data-stu-id="5593d-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="5593d-108">[in]以位元組為單位的大小`pbPublicKeyOrToken`。</span><span class="sxs-lookup"><span data-stu-id="5593d-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="5593d-109">[in]組件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="5593d-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="5593d-110">此值不得超過 1024年個字元。</span><span class="sxs-lookup"><span data-stu-id="5593d-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5593d-111">[in]ASSEMBLYMETADATA 執行個體，其中包含參考的組件的版本、 平台和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="5593d-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="5593d-112">[in]雜湊相關聯的資料與參考的組件。</span><span class="sxs-lookup"><span data-stu-id="5593d-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="5593d-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5593d-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="5593d-114">[in]以位元組為單位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="5593d-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="5593d-115">[in]位元組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)影響行為的執行引擎的值。</span><span class="sxs-lookup"><span data-stu-id="5593d-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="5593d-116">[out]所傳回的指標`AssemblyRef`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5593d-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5593d-117">備註</span><span class="sxs-lookup"><span data-stu-id="5593d-117">Remarks</span></span>  
 <span data-ttu-id="5593d-118">一個`AssemblyRef`必須定義這個組件參考的每個組件的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="5593d-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="5593d-119">在執行階段，參考的組件的詳細資料會傳遞至組件解析程式，並指出它們代表的"as 建置 」 的資訊。</span><span class="sxs-lookup"><span data-stu-id="5593d-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="5593d-120">組件解析程式接著會套用原則。</span><span class="sxs-lookup"><span data-stu-id="5593d-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5593d-121">需求</span><span class="sxs-lookup"><span data-stu-id="5593d-121">Requirements</span></span>  
 <span data-ttu-id="5593d-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5593d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5593d-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5593d-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5593d-124">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5593d-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5593d-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5593d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5593d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5593d-126">See also</span></span>

- [<span data-ttu-id="5593d-127">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5593d-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
