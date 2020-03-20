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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177893"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="daa42-102">IMetaDataAssemblyEmit::DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="daa42-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="daa42-103">創建包含`Assembly`指定組件中繼資料的結構並返回關聯的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="daa42-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daa42-104">語法</span><span class="sxs-lookup"><span data-stu-id="daa42-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="daa42-105">參數</span><span class="sxs-lookup"><span data-stu-id="daa42-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="daa42-106">[在]標識程式集的發行者的公共金鑰，如果程式集未強命名，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="daa42-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="daa42-107">[在]的大小（以位元組為單位）。 `pbPublicKey`</span><span class="sxs-lookup"><span data-stu-id="daa42-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="daa42-108">[在]用於加密程式集中的檔的雜湊演算法的識別碼，或用於指定 SHA-1 演算法的 Null。</span><span class="sxs-lookup"><span data-stu-id="daa42-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="daa42-109">[在]程式集的人類可讀文本名稱。</span><span class="sxs-lookup"><span data-stu-id="daa42-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="daa42-110">此值不得超過 1024 個字元。</span><span class="sxs-lookup"><span data-stu-id="daa42-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="daa42-111">[在]指向 ASSEMBLYMETADATA 實例的指標，其中包含程式集的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="daa42-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="daa42-112">[在]描述程式集功能的[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值的組合。</span><span class="sxs-lookup"><span data-stu-id="daa42-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="daa42-113">[出]指向中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="daa42-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daa42-114">備註</span><span class="sxs-lookup"><span data-stu-id="daa42-114">Remarks</span></span>  
 <span data-ttu-id="daa42-115">只能在清單`Assembly`中定義一個元資料結構。</span><span class="sxs-lookup"><span data-stu-id="daa42-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daa42-116">需求</span><span class="sxs-lookup"><span data-stu-id="daa42-116">Requirements</span></span>  
 <span data-ttu-id="daa42-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="daa42-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daa42-118">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="daa42-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="daa42-119">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="daa42-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="daa42-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daa42-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa42-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daa42-121">See also</span></span>

- [<span data-ttu-id="daa42-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="daa42-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
