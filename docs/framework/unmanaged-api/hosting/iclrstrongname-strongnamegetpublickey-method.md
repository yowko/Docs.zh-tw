---
title: ICLRStrongName::StrongNameGetPublicKey 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5bd314b2b63474d2a1d159f74564e2d4ca13aef6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725543"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="e4cec-102">ICLRStrongName::StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="e4cec-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>

<span data-ttu-id="e4cec-103">從公開/私密金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="e4cec-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="e4cec-104">金鑰組可以在密碼編譯服務提供者中提供作為金鑰容器名稱， (CSP) 或原始的位元組集合。</span><span class="sxs-lookup"><span data-stu-id="e4cec-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4cec-105">語法</span><span class="sxs-lookup"><span data-stu-id="e4cec-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4cec-106">參數</span><span class="sxs-lookup"><span data-stu-id="e4cec-106">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="e4cec-107">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="e4cec-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="e4cec-108">如果 `pbKeyBlob` 是 null，則 `szKeyContainer` 必須在 CSP 內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="e4cec-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="e4cec-109">在此情況下， [ICLRStrongName：： StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) 方法會從儲存在容器中的金鑰組解壓縮公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="e4cec-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="e4cec-110">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。</span><span class="sxs-lookup"><span data-stu-id="e4cec-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="e4cec-111">金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="e4cec-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="e4cec-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e4cec-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="e4cec-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="e4cec-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="e4cec-114">此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="e4cec-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="e4cec-115">如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `szKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="e4cec-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="e4cec-116">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="e4cec-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="e4cec-117">擴展傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="e4cec-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="e4cec-118">`ppbPublicKeyBlob`參數是由 common language runtime 所配置，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="e4cec-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="e4cec-119">呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="e4cec-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="e4cec-120">擴展傳回之公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="e4cec-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4cec-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="e4cec-121">Return Value</span></span>  

 <span data-ttu-id="e4cec-122">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="e4cec-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4cec-123">備註</span><span class="sxs-lookup"><span data-stu-id="e4cec-123">Remarks</span></span>  

 <span data-ttu-id="e4cec-124">公開金鑰包含在 [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) 結構中。</span><span class="sxs-lookup"><span data-stu-id="e4cec-124">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4cec-125">需求</span><span class="sxs-lookup"><span data-stu-id="e4cec-125">Requirements</span></span>  

 <span data-ttu-id="e4cec-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4cec-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4cec-127">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="e4cec-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e4cec-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e4cec-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4cec-129">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4cec-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cec-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4cec-130">See also</span></span>

- [<span data-ttu-id="e4cec-131">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="e4cec-131">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="e4cec-132">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="e4cec-132">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="e4cec-133">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e4cec-133">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
