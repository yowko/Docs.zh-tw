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
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181928"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="afa09-102">ICLRStrongName::StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="afa09-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="afa09-103">從公開金鑰/私密金鑰對獲取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="afa09-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="afa09-104">金鑰組可以作為加密服務提供者 （CSP） 中的金鑰容器名稱提供，也可以作為位元組的原創組合提供。</span><span class="sxs-lookup"><span data-stu-id="afa09-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa09-105">語法</span><span class="sxs-lookup"><span data-stu-id="afa09-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afa09-106">參數</span><span class="sxs-lookup"><span data-stu-id="afa09-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="afa09-107">[在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="afa09-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="afa09-108">如果`pbKeyBlob`為 null，`szKeyContainer`則必須在 CSP 中指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="afa09-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="afa09-109">在這種情況下[，ICLRStrongNameName：：StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法從存儲在容器中的金鑰組中提取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="afa09-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="afa09-110">如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。</span><span class="sxs-lookup"><span data-stu-id="afa09-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="afa09-111">金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。</span><span class="sxs-lookup"><span data-stu-id="afa09-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="afa09-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="afa09-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="afa09-113">[在]指向公開金鑰/私密金鑰對的指標。</span><span class="sxs-lookup"><span data-stu-id="afa09-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="afa09-114">此對採用 Win32`CryptExportKey`函數創建的格式。</span><span class="sxs-lookup"><span data-stu-id="afa09-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="afa09-115">如果`pbKeyBlob`為 null，則假定 指定的`szKeyContainer`鍵容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="afa09-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="afa09-116">[在]的大小（以位元組為單位）的大小`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="afa09-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="afa09-117">[出]返回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="afa09-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="afa09-118">參數`ppbPublicKeyBlob`由通用語言運行時分配並返回到調用方。</span><span class="sxs-lookup"><span data-stu-id="afa09-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="afa09-119">調用方必須使用[ICLRStrongNameName：：StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="afa09-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="afa09-120">[出]返回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="afa09-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afa09-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="afa09-121">Return Value</span></span>  
 <span data-ttu-id="afa09-122">`S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="afa09-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afa09-123">備註</span><span class="sxs-lookup"><span data-stu-id="afa09-123">Remarks</span></span>  
 <span data-ttu-id="afa09-124">公開金鑰包含在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構中。</span><span class="sxs-lookup"><span data-stu-id="afa09-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afa09-125">需求</span><span class="sxs-lookup"><span data-stu-id="afa09-125">Requirements</span></span>  
 <span data-ttu-id="afa09-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="afa09-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afa09-127">**標題：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="afa09-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="afa09-128">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="afa09-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afa09-129">**.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afa09-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa09-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afa09-130">See also</span></span>

- [<span data-ttu-id="afa09-131">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="afa09-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="afa09-132">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="afa09-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="afa09-133">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="afa09-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
