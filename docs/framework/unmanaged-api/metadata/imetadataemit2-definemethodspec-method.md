---
title: IMetaDataEmit2::DefineMethodSpec 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4185ec41fc9f7d1d919a79b57c02625210ad72a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777188"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="8f127-102">IMetaDataEmit2::DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="8f127-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="8f127-103">建立泛型方法的執行個體，並取得定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8f127-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f127-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f127-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f127-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f127-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="8f127-106">[in]要建立一般的執行個體方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8f127-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="8f127-107">語彙基元必須是型別`mdMethodDef`或`mdMemberRef`。</span><span class="sxs-lookup"><span data-stu-id="8f127-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8f127-108">[in]二進位 COM + 方法的簽章指標。</span><span class="sxs-lookup"><span data-stu-id="8f127-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="8f127-109">[in]大小，以位元組為單位的`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="8f127-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="8f127-110">[out]方法的中繼資料簽章定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8f127-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f127-111">需求</span><span class="sxs-lookup"><span data-stu-id="8f127-111">Requirements</span></span>  
 <span data-ttu-id="8f127-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f127-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f127-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8f127-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f127-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8f127-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f127-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f127-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f127-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f127-116">See also</span></span>

- [<span data-ttu-id="8f127-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8f127-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8f127-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8f127-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
