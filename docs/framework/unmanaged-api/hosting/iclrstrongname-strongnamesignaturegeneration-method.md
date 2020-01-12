---
title: ICLRStrongName::StrongNameSignatureGeneration 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: ced7540afe931fb91240c770d76d205400157a51
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901094"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="114bb-102">ICLRStrongName::StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="114bb-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="114bb-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="114bb-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="114bb-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="114bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="114bb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="114bb-106">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="114bb-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="114bb-107">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="114bb-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="114bb-108">如果 `pbKeyBlob` 為 null，`wszKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="114bb-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="114bb-109">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="114bb-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="114bb-110">如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="114bb-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="114bb-111">金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="114bb-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="114bb-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="114bb-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="114bb-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="114bb-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="114bb-114">這組會使用 Win32 `CryptExportKey` 函式所建立的格式。</span><span class="sxs-lookup"><span data-stu-id="114bb-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="114bb-115">如果 `pbKeyBlob` 是 null，則會假設 `wszKeyContainer` 指定的金鑰容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="114bb-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="114bb-116">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="114bb-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="114bb-117">脫銷通用語言執行時間傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="114bb-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="114bb-118">如果 `ppbSignatureBlob` 為 null，執行時間會將簽章儲存在 `wszFilePath`所指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="114bb-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="114bb-119">如果 `ppbSignatureBlob` 不是 null，通用語言執行時間會配置用來傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="114bb-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="114bb-120">呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="114bb-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="114bb-121">脫銷所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="114bb-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="114bb-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="114bb-122">Return Value</span></span>  
 <span data-ttu-id="114bb-123">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="114bb-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="114bb-124">備註</span><span class="sxs-lookup"><span data-stu-id="114bb-124">Remarks</span></span>  
 <span data-ttu-id="114bb-125">為 `wszFilePath` 指定 null 以計算簽章的大小，而不建立簽章。</span><span class="sxs-lookup"><span data-stu-id="114bb-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="114bb-126">簽章可以直接儲存在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="114bb-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="114bb-127">需求</span><span class="sxs-lookup"><span data-stu-id="114bb-127">Requirements</span></span>  
 <span data-ttu-id="114bb-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="114bb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="114bb-129">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="114bb-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="114bb-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="114bb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="114bb-131">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="114bb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114bb-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="114bb-132">See also</span></span>

- [<span data-ttu-id="114bb-133">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="114bb-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="114bb-134">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="114bb-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
