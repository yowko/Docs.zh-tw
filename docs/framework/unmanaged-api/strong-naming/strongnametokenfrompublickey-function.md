---
title: StrongNameTokenFromPublicKey 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb8ff76da288975ef291d226bb1f205e73a64252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460284"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="05aff-102">StrongNameTokenFromPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="05aff-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="05aff-103">取得代表公開金鑰的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="05aff-103">Gets a token representing a public key.</span></span> <span data-ttu-id="05aff-104">為強式名稱語彙基元是公開金鑰縮短形式。</span><span class="sxs-lookup"><span data-stu-id="05aff-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="05aff-105">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="05aff-105">This function has been deprecated.</span></span> <span data-ttu-id="05aff-106">使用[iclrstrongname:: Strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="05aff-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05aff-107">語法</span><span class="sxs-lookup"><span data-stu-id="05aff-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05aff-108">參數</span><span class="sxs-lookup"><span data-stu-id="05aff-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="05aff-109">[in]型別的結構[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) ，其中包含用來產生強式名稱簽章金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="05aff-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="05aff-110">[in]大小，以位元組為單位的`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="05aff-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="05aff-111">[out]對應到索引鍵的強式名稱語彙基元傳入`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="05aff-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="05aff-112">Common language runtime 配置的記憶體，以傳回語彙基元。</span><span class="sxs-lookup"><span data-stu-id="05aff-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="05aff-113">呼叫端必須釋放這個記憶體使用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="05aff-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="05aff-114">[out]大小，以位元組為單位傳回強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="05aff-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05aff-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="05aff-115">Return Value</span></span>  
 <span data-ttu-id="05aff-116">`true` 如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="05aff-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05aff-117">備註</span><span class="sxs-lookup"><span data-stu-id="05aff-117">Remarks</span></span>  
 <span data-ttu-id="05aff-118">為強式名稱語彙基元是公開金鑰的用來將索引鍵資訊儲存在中繼資料時，儲存空間縮短形式。</span><span class="sxs-lookup"><span data-stu-id="05aff-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="05aff-119">具體來說，強式名稱語彙基元會在組件參考中用來參考相依組件。</span><span class="sxs-lookup"><span data-stu-id="05aff-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="05aff-120">如果`StrongNameTokenFromPublicKey`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="05aff-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05aff-121">需求</span><span class="sxs-lookup"><span data-stu-id="05aff-121">Requirements</span></span>  
 <span data-ttu-id="05aff-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05aff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05aff-123">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="05aff-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="05aff-124">**程式庫：** 包含做為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="05aff-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="05aff-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05aff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05aff-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05aff-126">See Also</span></span>  
 [<span data-ttu-id="05aff-127">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="05aff-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="05aff-128">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="05aff-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="05aff-129">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="05aff-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
