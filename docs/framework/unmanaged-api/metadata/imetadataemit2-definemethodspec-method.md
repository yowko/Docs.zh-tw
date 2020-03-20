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
ms.openlocfilehash: a5d9342b8bfe650106ccf9daf2a91dfbcd575446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175534"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="49bfb-102">IMetaDataEmit2::DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="49bfb-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="49bfb-103">創建方法的泛型實例，並獲取定義中的權杖。</span><span class="sxs-lookup"><span data-stu-id="49bfb-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49bfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="49bfb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49bfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="49bfb-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="49bfb-106">[在]用於創建泛型實例的方法的權杖。</span><span class="sxs-lookup"><span data-stu-id="49bfb-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="49bfb-107">權杖必須為 類型`mdMethodDef`或`mdMemberRef`。</span><span class="sxs-lookup"><span data-stu-id="49bfb-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="49bfb-108">[在]指向方法的二進位 COM+ 簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="49bfb-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="49bfb-109">[在]的大小（以位元組為單位）的大小`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="49bfb-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="49bfb-110">[出]方法的中繼資料簽名定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="49bfb-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49bfb-111">需求</span><span class="sxs-lookup"><span data-stu-id="49bfb-111">Requirements</span></span>  
 <span data-ttu-id="49bfb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49bfb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49bfb-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="49bfb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49bfb-114">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="49bfb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49bfb-115">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49bfb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bfb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49bfb-116">See also</span></span>

- [<span data-ttu-id="49bfb-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="49bfb-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="49bfb-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="49bfb-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
