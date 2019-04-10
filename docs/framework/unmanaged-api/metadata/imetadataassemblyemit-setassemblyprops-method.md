---
title: IMetaDataAssemblyEmit::SetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3361212f9a7f7ff0739e8544419a2b67abc8f457
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214646"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="5343c-102">IMetaDataAssemblyEmit::SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="5343c-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="5343c-103">修改指定的 `Assembly` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="5343c-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5343c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5343c-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5343c-105">參數</span><span class="sxs-lookup"><span data-stu-id="5343c-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="5343c-106">[in]指定中繼資料語彙基元`Assembly`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="5343c-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="5343c-107">[in]組件的 「 發行者 」 的公開的索引鍵的指標。</span><span class="sxs-lookup"><span data-stu-id="5343c-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="5343c-108">[in]以位元組為單位的大小`pbPublicKey`。</span><span class="sxs-lookup"><span data-stu-id="5343c-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="5343c-109">[in]用來雜湊的組件檔案的雜湊演算法識別項。</span><span class="sxs-lookup"><span data-stu-id="5343c-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="5343c-110">[in]組件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="5343c-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5343c-111">[in]包含組件的版本、 平台，以及地區設定資訊 ASSEMBLYMETADATA 指標。</span><span class="sxs-lookup"><span data-stu-id="5343c-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="5343c-112">[in]位元組合[AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)指定組件的各種屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5343c-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5343c-113">備註</span><span class="sxs-lookup"><span data-stu-id="5343c-113">Remarks</span></span>  
 <span data-ttu-id="5343c-114">若要建立`Assembly`中繼資料結構，使用[imetadataassemblyemit:: Defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5343c-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5343c-115">需求</span><span class="sxs-lookup"><span data-stu-id="5343c-115">Requirements</span></span>  
 <span data-ttu-id="5343c-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5343c-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5343c-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5343c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5343c-118">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5343c-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5343c-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5343c-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5343c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5343c-120">See also</span></span>

- [<span data-ttu-id="5343c-121">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5343c-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
