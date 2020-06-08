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
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503812"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="c6342-102">IMetaDataEmit2::DefineMethodSpec 方法</span><span class="sxs-lookup"><span data-stu-id="c6342-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="c6342-103">建立方法的泛型實例，並取得定義的 token。</span><span class="sxs-lookup"><span data-stu-id="c6342-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6342-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6342-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6342-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6342-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="c6342-106">在要建立泛型實例之方法的 token。</span><span class="sxs-lookup"><span data-stu-id="c6342-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="c6342-107">Token 的類型必須是 `mdMethodDef` 或 `mdMemberRef` 。</span><span class="sxs-lookup"><span data-stu-id="c6342-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c6342-108">在方法之二進位 COM + 簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="c6342-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="c6342-109">在的大小（以位元組為單位） `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="c6342-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="c6342-110">脫銷方法之中繼資料簽章定義的 token。</span><span class="sxs-lookup"><span data-stu-id="c6342-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6342-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="c6342-111">Requirements</span></span>  
 <span data-ttu-id="c6342-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6342-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6342-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c6342-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6342-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c6342-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6342-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6342-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6342-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6342-116">See also</span></span>

- [<span data-ttu-id="c6342-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c6342-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="c6342-118">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c6342-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
