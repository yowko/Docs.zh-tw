---
title: StrongNameGetPublicKey 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: 966a2a628f30f1999688da7b6ba435c1d6cb830c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094656"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="1d0ba-102">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="1d0ba-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="1d0ba-103">從私密/公開金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="1d0ba-104">金鑰組可以提供為密碼編譯服務提供者（CSP）內的金鑰容器名稱，或做為原始的位元組集合。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="1d0ba-105">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-105">This function has been deprecated.</span></span> <span data-ttu-id="1d0ba-106">請改用[ICLRStrongName：： StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0ba-107">語法</span><span class="sxs-lookup"><span data-stu-id="1d0ba-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d0ba-108">參數</span><span class="sxs-lookup"><span data-stu-id="1d0ba-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="1d0ba-109">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="1d0ba-110">如果 `pbKeyBlob` 為 null，`szKeyContainer` 必須在 CSP 內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="1d0ba-111">在此情況下，`StrongNameGetPublicKey` 會從儲存在容器中的金鑰組中解壓縮公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="1d0ba-112">如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="1d0ba-113">金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="1d0ba-114">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1d0ba-115">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1d0ba-116">這組會使用 Win32 `CryptExportKey` 函式所建立的格式。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1d0ba-117">如果 `pbKeyBlob` 是 null，則會假設 `szKeyContainer` 指定的金鑰容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1d0ba-118">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="1d0ba-119">脫銷傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="1d0ba-120">`ppbPublicKeyBlob` 參數是由 common language runtime 所配置，並會傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="1d0ba-121">呼叫端必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="1d0ba-122">脫銷傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d0ba-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="1d0ba-123">Return Value</span></span>  
 <span data-ttu-id="1d0ba-124">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d0ba-125">備註</span><span class="sxs-lookup"><span data-stu-id="1d0ba-125">Remarks</span></span>  
 <span data-ttu-id="1d0ba-126">公開金鑰包含在[PublicKeyBlob](publickeyblob-structure.md)結構中。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="1d0ba-127">如果 `StrongNameGetPublicKey` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d0ba-128">需求</span><span class="sxs-lookup"><span data-stu-id="1d0ba-128">Requirements</span></span>  
 <span data-ttu-id="1d0ba-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d0ba-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d0ba-130">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="1d0ba-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1d0ba-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1d0ba-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d0ba-132">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d0ba-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0ba-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d0ba-133">See also</span></span>

- [<span data-ttu-id="1d0ba-134">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="1d0ba-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="1d0ba-135">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="1d0ba-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="1d0ba-136">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1d0ba-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="1d0ba-137">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="1d0ba-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
