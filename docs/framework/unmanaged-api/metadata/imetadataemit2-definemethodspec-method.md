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
ms.openlocfilehash: 817b3a18b047bfca1f3a7c7099920a12e6253f58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712829"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="4c580-102">IMetaDataEmit2::DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="4c580-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>

<span data-ttu-id="4c580-103">建立方法的泛型實例，並取得定義的標記。</span><span class="sxs-lookup"><span data-stu-id="4c580-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c580-104">語法</span><span class="sxs-lookup"><span data-stu-id="4c580-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c580-105">參數</span><span class="sxs-lookup"><span data-stu-id="4c580-105">Parameters</span></span>  

 `tkParent`  
 <span data-ttu-id="4c580-106">在要建立泛型實例之方法的標記。</span><span class="sxs-lookup"><span data-stu-id="4c580-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="4c580-107">標記的類型必須是 `mdMethodDef` 或 `mdMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="4c580-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4c580-108">在方法的二進位 COM + 簽章指標。</span><span class="sxs-lookup"><span data-stu-id="4c580-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="4c580-109">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="4c580-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="4c580-110">擴展方法的中繼資料簽章定義標記。</span><span class="sxs-lookup"><span data-stu-id="4c580-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c580-111">需求</span><span class="sxs-lookup"><span data-stu-id="4c580-111">Requirements</span></span>  

 <span data-ttu-id="4c580-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c580-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c580-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4c580-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c580-114">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4c580-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c580-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c580-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c580-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c580-116">See also</span></span>

- [<span data-ttu-id="4c580-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4c580-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="4c580-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4c580-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
