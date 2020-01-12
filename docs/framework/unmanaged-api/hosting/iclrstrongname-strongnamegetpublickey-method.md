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
ms.openlocfilehash: fd7f95ea01de397509c2a7b5fc08c0ac401a8da9
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899601"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="47f11-102">ICLRStrongName::StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="47f11-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="47f11-103">從公開/私密金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="47f11-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="47f11-104">金鑰組可以提供為密碼編譯服務提供者（CSP）內的金鑰容器名稱，或做為原始的位元組集合。</span><span class="sxs-lookup"><span data-stu-id="47f11-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f11-105">語法</span><span class="sxs-lookup"><span data-stu-id="47f11-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47f11-106">參數</span><span class="sxs-lookup"><span data-stu-id="47f11-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="47f11-107">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="47f11-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="47f11-108">如果 `pbKeyBlob` 為 null，`szKeyContainer` 必須在 CSP 內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="47f11-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="47f11-109">在此情況下， [ICLRStrongName：： StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法會從儲存在容器中的金鑰組中，抽取出公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="47f11-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="47f11-110">如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="47f11-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="47f11-111">金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="47f11-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="47f11-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="47f11-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="47f11-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="47f11-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="47f11-114">這組會使用 Win32 `CryptExportKey` 函式所建立的格式。</span><span class="sxs-lookup"><span data-stu-id="47f11-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="47f11-115">如果 `pbKeyBlob` 是 null，則會假設 `szKeyContainer` 指定的金鑰容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="47f11-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="47f11-116">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="47f11-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="47f11-117">脫銷傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="47f11-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="47f11-118">`ppbPublicKeyBlob` 參數是由 common language runtime 所配置，並會傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="47f11-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="47f11-119">呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="47f11-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="47f11-120">脫銷傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="47f11-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47f11-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="47f11-121">Return Value</span></span>  
 <span data-ttu-id="47f11-122">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="47f11-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47f11-123">備註</span><span class="sxs-lookup"><span data-stu-id="47f11-123">Remarks</span></span>  
 <span data-ttu-id="47f11-124">公開金鑰包含在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構中。</span><span class="sxs-lookup"><span data-stu-id="47f11-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f11-125">需求</span><span class="sxs-lookup"><span data-stu-id="47f11-125">Requirements</span></span>  
 <span data-ttu-id="47f11-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47f11-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47f11-127">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="47f11-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47f11-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="47f11-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47f11-129">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47f11-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f11-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="47f11-130">See also</span></span>

- [<span data-ttu-id="47f11-131">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="47f11-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="47f11-132">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="47f11-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="47f11-133">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="47f11-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
