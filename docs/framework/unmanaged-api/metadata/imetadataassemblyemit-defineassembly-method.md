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
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008179"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="01371-102">IMetaDataAssemblyEmit::DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="01371-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="01371-103">建立 `Assembly` 包含指定元件之中繼資料的結構，並傳回相關聯的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="01371-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01371-104">語法</span><span class="sxs-lookup"><span data-stu-id="01371-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="01371-105">參數</span><span class="sxs-lookup"><span data-stu-id="01371-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="01371-106">在識別元件發行者的公開金鑰; 如果元件不是強式名稱，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="01371-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="01371-107">在的大小（以位元組為單位） `pbPublicKey` 。</span><span class="sxs-lookup"><span data-stu-id="01371-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="01371-108">在要用來加密元件中之檔案的雜湊演算法識別碼，或為 Null 以指定 SHA-1 演算法。</span><span class="sxs-lookup"><span data-stu-id="01371-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="01371-109">在元件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="01371-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="01371-110">此值不得超過1024個字元。</span><span class="sxs-lookup"><span data-stu-id="01371-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="01371-111">在ASSEMBLYMETADATA 實例的指標，其中包含元件的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="01371-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="01371-112">在描述元件功能的[CorAssemblyFlags](corassemblyflags-enumeration.md)值組合。</span><span class="sxs-lookup"><span data-stu-id="01371-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="01371-113">脫銷元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="01371-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01371-114">備註</span><span class="sxs-lookup"><span data-stu-id="01371-114">Remarks</span></span>  
 <span data-ttu-id="01371-115">`Assembly`資訊清單中只能定義一個元資料結構。</span><span class="sxs-lookup"><span data-stu-id="01371-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01371-116">需求</span><span class="sxs-lookup"><span data-stu-id="01371-116">Requirements</span></span>  
 <span data-ttu-id="01371-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01371-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01371-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="01371-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01371-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="01371-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01371-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01371-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01371-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01371-121">See also</span></span>

- [<span data-ttu-id="01371-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="01371-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
