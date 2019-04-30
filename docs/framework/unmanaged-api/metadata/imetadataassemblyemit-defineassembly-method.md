---
title: IMetaDataAssemblyEmit::DefineAssembly 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b95a583aec87e3ba3e247d1ef800302b62657837
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044820"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="1b947-102">IMetaDataAssemblyEmit::DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1b947-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="1b947-103">建立`Assembly`結構指定的組件包含中繼資料，並傳回相關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1b947-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b947-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b947-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1b947-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b947-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="1b947-106">[in]如果不具備強式名稱組件識別的組件或 NULL 發行者公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="1b947-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="1b947-107">[in]以位元組為單位的大小`pbPublicKey`。</span><span class="sxs-lookup"><span data-stu-id="1b947-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="1b947-108">[in]用來加密組件或 NULL，指定 sha-1 演算法中的檔案雜湊演算法的識別項。</span><span class="sxs-lookup"><span data-stu-id="1b947-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="1b947-109">[in]組件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="1b947-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="1b947-110">此值不得超過 1024年個字元。</span><span class="sxs-lookup"><span data-stu-id="1b947-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1b947-111">[in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊的指標。</span><span class="sxs-lookup"><span data-stu-id="1b947-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="1b947-112">[in]組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值，描述組件的功能。</span><span class="sxs-lookup"><span data-stu-id="1b947-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="1b947-113">[out]中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="1b947-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b947-114">備註</span><span class="sxs-lookup"><span data-stu-id="1b947-114">Remarks</span></span>  
 <span data-ttu-id="1b947-115">只有一個`Assembly`中繼資料結構可以定義資訊清單內。</span><span class="sxs-lookup"><span data-stu-id="1b947-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b947-116">需求</span><span class="sxs-lookup"><span data-stu-id="1b947-116">Requirements</span></span>  
 <span data-ttu-id="1b947-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b947-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b947-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b947-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b947-119">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1b947-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b947-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b947-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b947-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b947-121">See also</span></span>

- [<span data-ttu-id="1b947-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1b947-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
