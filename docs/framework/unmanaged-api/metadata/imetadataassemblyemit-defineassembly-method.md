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
ms.openlocfilehash: 6d783e27c60db7381025f3b2382728e3996323ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725725"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="33515-102">IMetaDataAssemblyEmit::DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="33515-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>

<span data-ttu-id="33515-103">建立 `Assembly` 包含指定元件之中繼資料的結構，並傳回相關聯的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="33515-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33515-104">語法</span><span class="sxs-lookup"><span data-stu-id="33515-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="33515-105">參數</span><span class="sxs-lookup"><span data-stu-id="33515-105">Parameters</span></span>  

 `pbPublicKey`  
 <span data-ttu-id="33515-106">在識別元件發行者的公開金鑰; 如果元件不是強式名稱，則為 Null。</span><span class="sxs-lookup"><span data-stu-id="33515-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="33515-107">在的大小（以位元組為單位） `pbPublicKey` 。</span><span class="sxs-lookup"><span data-stu-id="33515-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="33515-108">在用來加密元件中之檔案的雜湊演算法識別碼，或 Null 以指定 SHA-1 演算法。</span><span class="sxs-lookup"><span data-stu-id="33515-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="33515-109">在元件的人們可讀取文字名稱。</span><span class="sxs-lookup"><span data-stu-id="33515-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="33515-110">此值不得超過1024個字元。</span><span class="sxs-lookup"><span data-stu-id="33515-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="33515-111">在ASSEMBLYMETADATA 實例的指標，其中包含元件的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="33515-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="33515-112">在描述元件功能的 [CorAssemblyFlags](corassemblyflags-enumeration.md) 值組合。</span><span class="sxs-lookup"><span data-stu-id="33515-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="33515-113">擴展元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="33515-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33515-114">備註</span><span class="sxs-lookup"><span data-stu-id="33515-114">Remarks</span></span>  

 <span data-ttu-id="33515-115">只有一個 `Assembly` 元資料結構可以在資訊清單中定義。</span><span class="sxs-lookup"><span data-stu-id="33515-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33515-116">需求</span><span class="sxs-lookup"><span data-stu-id="33515-116">Requirements</span></span>  

 <span data-ttu-id="33515-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33515-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33515-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="33515-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33515-119">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="33515-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33515-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33515-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33515-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33515-121">See also</span></span>

- [<span data-ttu-id="33515-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="33515-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
