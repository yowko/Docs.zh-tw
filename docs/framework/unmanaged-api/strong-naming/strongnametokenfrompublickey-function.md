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
ms.openlocfilehash: 197504cbb0dd66c0cf43dee718026fc63e918d60
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798858"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="99aa9-102">StrongNameTokenFromPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="99aa9-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="99aa9-103">取得代表公開金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="99aa9-103">Gets a token representing a public key.</span></span> <span data-ttu-id="99aa9-104">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="99aa9-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="99aa9-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="99aa9-105">This function has been deprecated.</span></span> <span data-ttu-id="99aa9-106">請改用[ICLRStrongName：： StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="99aa9-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99aa9-107">語法</span><span class="sxs-lookup"><span data-stu-id="99aa9-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99aa9-108">參數</span><span class="sxs-lookup"><span data-stu-id="99aa9-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="99aa9-109">在[PublicKeyBlob](publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="99aa9-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="99aa9-110">在的大小（以位元組為單位`pbPublicKeyBlob`）。</span><span class="sxs-lookup"><span data-stu-id="99aa9-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="99aa9-111">脫銷對應至傳入`pbPublicKeyBlob`之金鑰的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="99aa9-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="99aa9-112">Common language runtime 會配置要在其中傳回 token 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="99aa9-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="99aa9-113">呼叫端必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="99aa9-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="99aa9-114">脫銷傳回之強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="99aa9-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99aa9-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="99aa9-115">Return Value</span></span>  
 <span data-ttu-id="99aa9-116">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="99aa9-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99aa9-117">備註</span><span class="sxs-lookup"><span data-stu-id="99aa9-117">Remarks</span></span>  
 <span data-ttu-id="99aa9-118">強式名稱 token 是在將金鑰資訊儲存在中繼資料中時，用來節省空間的公用金鑰的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="99aa9-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="99aa9-119">具體而言，強式名稱標記會在元件參考中用來參考相依元件。</span><span class="sxs-lookup"><span data-stu-id="99aa9-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="99aa9-120">如果 `StrongNameTokenFromPublicKey` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="99aa9-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99aa9-121">需求</span><span class="sxs-lookup"><span data-stu-id="99aa9-121">Requirements</span></span>  
 <span data-ttu-id="99aa9-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99aa9-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99aa9-123">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="99aa9-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="99aa9-124">**LIBRARY:** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="99aa9-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="99aa9-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99aa9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99aa9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99aa9-126">See also</span></span>

- [<span data-ttu-id="99aa9-127">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="99aa9-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="99aa9-128">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="99aa9-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="99aa9-129">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="99aa9-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
