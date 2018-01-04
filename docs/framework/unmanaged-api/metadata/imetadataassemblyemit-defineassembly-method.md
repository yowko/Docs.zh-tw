---
title: "IMetaDataAssemblyEmit::DefineAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="c5ed9-102">IMetaDataAssemblyEmit::DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c5ed9-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="c5ed9-103">建立`Assembly`結構包含其中繼資料的指定組件，並傳回相關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ed9-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5ed9-104">Syntax</span></span>  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5ed9-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5ed9-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="c5ed9-106">[in]識別發行者的組件或為 NULL，如果組件不具備強式名稱公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="c5ed9-107">[in]以位元組為單位的大小`pbPublicKey`。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="c5ed9-108">[in]用來加密的檔案中的組件或為 NULL 來指定 sha-1 演算法的雜湊演算法識別項。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5ed9-109">[in]人類看得懂的文字之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="c5ed9-110">此值不能超過 1024年個字元。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c5ed9-111">[in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊指標。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="c5ed9-112">[in]組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值描述組件的功能。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="c5ed9-113">[out]中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5ed9-114">備註</span><span class="sxs-lookup"><span data-stu-id="c5ed9-114">Remarks</span></span>  
 <span data-ttu-id="c5ed9-115">只有一個`Assembly`可以定義清單內的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ed9-116">需求</span><span class="sxs-lookup"><span data-stu-id="c5ed9-116">Requirements</span></span>  
 <span data-ttu-id="c5ed9-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5ed9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5ed9-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5ed9-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5ed9-119">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c5ed9-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5ed9-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ed9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ed9-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5ed9-121">See Also</span></span>  
 [<span data-ttu-id="c5ed9-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c5ed9-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
