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
ms.openlocfilehash: 8cc28d9ccd40c65d225a96b269562c9d3dfa2124
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729885"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="1e48e-102">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="1e48e-102">StrongNameGetPublicKeyEx Method</span></span>

<span data-ttu-id="1e48e-103">從公開/私密金鑰組取得公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="1e48e-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e48e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e48e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1e48e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e48e-105">Parameters</span></span>  

 `pwzKeyContainer`  
 <span data-ttu-id="1e48e-106">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1e48e-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="1e48e-107">如果 `pbKeyBlob` 是 null，則 `szKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。</span><span class="sxs-lookup"><span data-stu-id="1e48e-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="1e48e-108">在此情況下， `StrongNameGetPublicKeyEx` 方法會從儲存在容器中的金鑰組解壓縮公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e48e-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="1e48e-109">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。</span><span class="sxs-lookup"><span data-stu-id="1e48e-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="1e48e-110">金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e48e-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="1e48e-111">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e48e-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1e48e-112">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="1e48e-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1e48e-113">此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="1e48e-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1e48e-114">如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `szKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1e48e-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1e48e-115">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="1e48e-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="1e48e-116">擴展傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="1e48e-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="1e48e-117">`ppbPublicKeyBlob`參數是由 common language runtime 所配置，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="1e48e-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="1e48e-118">呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="1e48e-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="1e48e-119">擴展傳回之公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="1e48e-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="1e48e-120">在元件雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="1e48e-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="1e48e-121">如需接受值的清單，請參閱「備註」一節。</span><span class="sxs-lookup"><span data-stu-id="1e48e-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="1e48e-122">在保留供日後使用;預設值為 null。</span><span class="sxs-lookup"><span data-stu-id="1e48e-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e48e-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e48e-123">Return Value</span></span>  

 <span data-ttu-id="1e48e-124">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="1e48e-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e48e-125">備註</span><span class="sxs-lookup"><span data-stu-id="1e48e-125">Remarks</span></span>  

 <span data-ttu-id="1e48e-126">公開金鑰包含在 [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) 結構中。</span><span class="sxs-lookup"><span data-stu-id="1e48e-126">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e48e-127">備註</span><span class="sxs-lookup"><span data-stu-id="1e48e-127">Remarks</span></span>  

 <span data-ttu-id="1e48e-128">下表顯示參數接受的值集 `uHashAlgId` 。</span><span class="sxs-lookup"><span data-stu-id="1e48e-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="1e48e-129">名稱</span><span class="sxs-lookup"><span data-stu-id="1e48e-129">Name</span></span>|<span data-ttu-id="1e48e-130">值</span><span class="sxs-lookup"><span data-stu-id="1e48e-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="1e48e-131">None</span><span class="sxs-lookup"><span data-stu-id="1e48e-131">None</span></span>|<span data-ttu-id="1e48e-132">0</span><span class="sxs-lookup"><span data-stu-id="1e48e-132">0</span></span>|  
|<span data-ttu-id="1e48e-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="1e48e-133">SHA-1</span></span>|<span data-ttu-id="1e48e-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="1e48e-134">0x8004</span></span>|  
|<span data-ttu-id="1e48e-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="1e48e-135">SHA-256</span></span>|<span data-ttu-id="1e48e-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="1e48e-136">0x800c</span></span>|  
|<span data-ttu-id="1e48e-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="1e48e-137">SHA-384</span></span>|<span data-ttu-id="1e48e-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="1e48e-138">0x800d</span></span>|  
|<span data-ttu-id="1e48e-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="1e48e-139">SHA-512</span></span>|<span data-ttu-id="1e48e-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="1e48e-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e48e-141">需求</span><span class="sxs-lookup"><span data-stu-id="1e48e-141">Requirements</span></span>  

 <span data-ttu-id="1e48e-142">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e48e-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e48e-143">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="1e48e-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1e48e-144">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1e48e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e48e-145">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e48e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e48e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e48e-146">See also</span></span>

- [<span data-ttu-id="1e48e-147">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="1e48e-147">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="1e48e-148">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="1e48e-148">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="1e48e-149">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1e48e-149">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="1e48e-150">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="1e48e-150">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
