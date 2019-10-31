---
title: StrongNameGetPublicKeyEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 700bcc5b818c452d3642d325fb6fe19cbb162474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141454"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="13f03-102">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="13f03-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="13f03-103">從公開/私密金鑰組取得公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="13f03-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f03-104">語法</span><span class="sxs-lookup"><span data-stu-id="13f03-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13f03-105">參數</span><span class="sxs-lookup"><span data-stu-id="13f03-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="13f03-106">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="13f03-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="13f03-107">如果 `pbKeyBlob` 為 null，`szKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="13f03-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="13f03-108">在此情況下，`StrongNameGetPublicKeyEx` 方法會從儲存在容器中的金鑰組中，抽取出公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="13f03-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="13f03-109">如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="13f03-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="13f03-110">金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="13f03-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="13f03-111">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="13f03-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="13f03-112">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="13f03-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="13f03-113">這組會使用 Win32 `CryptExportKey` 函式所建立的格式。</span><span class="sxs-lookup"><span data-stu-id="13f03-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="13f03-114">如果 `pbKeyBlob` 是 null，則會假設 `szKeyContainer` 指定的金鑰容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="13f03-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="13f03-115">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="13f03-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="13f03-116">脫銷傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="13f03-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="13f03-117">`ppbPublicKeyBlob` 參數是由 common language runtime 所配置，並會傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="13f03-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="13f03-118">呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="13f03-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="13f03-119">脫銷傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="13f03-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="13f03-120">在元件雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="13f03-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="13f03-121">如需接受值的清單，請參閱備註一節。</span><span class="sxs-lookup"><span data-stu-id="13f03-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="13f03-122">在保留供日後使用;預設值為 null。</span><span class="sxs-lookup"><span data-stu-id="13f03-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13f03-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="13f03-123">Return Value</span></span>  
 <span data-ttu-id="13f03-124">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="13f03-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f03-125">備註</span><span class="sxs-lookup"><span data-stu-id="13f03-125">Remarks</span></span>  
 <span data-ttu-id="13f03-126">公開金鑰包含在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構中。</span><span class="sxs-lookup"><span data-stu-id="13f03-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f03-127">備註</span><span class="sxs-lookup"><span data-stu-id="13f03-127">Remarks</span></span>  
 <span data-ttu-id="13f03-128">下表顯示 `uHashAlgId` 參數的可接受值集。</span><span class="sxs-lookup"><span data-stu-id="13f03-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="13f03-129">[屬性]</span><span class="sxs-lookup"><span data-stu-id="13f03-129">Name</span></span>|<span data-ttu-id="13f03-130">值</span><span class="sxs-lookup"><span data-stu-id="13f03-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="13f03-131">None</span><span class="sxs-lookup"><span data-stu-id="13f03-131">None</span></span>|<span data-ttu-id="13f03-132">0</span><span class="sxs-lookup"><span data-stu-id="13f03-132">0</span></span>|  
|<span data-ttu-id="13f03-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="13f03-133">SHA-1</span></span>|<span data-ttu-id="13f03-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="13f03-134">0x8004</span></span>|  
|<span data-ttu-id="13f03-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="13f03-135">SHA-256</span></span>|<span data-ttu-id="13f03-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="13f03-136">0x800c</span></span>|  
|<span data-ttu-id="13f03-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="13f03-137">SHA-384</span></span>|<span data-ttu-id="13f03-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="13f03-138">0x800d</span></span>|  
|<span data-ttu-id="13f03-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="13f03-139">SHA-512</span></span>|<span data-ttu-id="13f03-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="13f03-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13f03-141">需求</span><span class="sxs-lookup"><span data-stu-id="13f03-141">Requirements</span></span>  
 <span data-ttu-id="13f03-142">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13f03-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f03-143">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="13f03-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="13f03-144">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="13f03-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13f03-145">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f03-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f03-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="13f03-146">See also</span></span>

- [<span data-ttu-id="13f03-147">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="13f03-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="13f03-148">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="13f03-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="13f03-149">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="13f03-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="13f03-150">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="13f03-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
