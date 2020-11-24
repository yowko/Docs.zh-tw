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
ms.openlocfilehash: 9fc517b081a1df48d943d03a9c3ce223a428bde7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671625"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="8f608-102">ICLRStrongName::StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="8f608-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>

<span data-ttu-id="8f608-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="8f608-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f608-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f608-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8f608-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f608-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="8f608-106">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="8f608-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="8f608-107">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="8f608-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="8f608-108">如果 `pbKeyBlob` 是 null，則 `wszKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。</span><span class="sxs-lookup"><span data-stu-id="8f608-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="8f608-109">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="8f608-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="8f608-110">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。</span><span class="sxs-lookup"><span data-stu-id="8f608-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="8f608-111">金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f608-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="8f608-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="8f608-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8f608-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="8f608-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8f608-114">此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="8f608-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8f608-115">如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="8f608-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8f608-116">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8f608-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="8f608-117">擴展Common language runtime 傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="8f608-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="8f608-118">如果 `ppbSignatureBlob` 是 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="8f608-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="8f608-119">如果不 `ppbSignatureBlob` 是 null，則 common language runtime 會配置要傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="8f608-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="8f608-120">呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="8f608-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="8f608-121">擴展所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8f608-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f608-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f608-122">Return Value</span></span>  

 <span data-ttu-id="8f608-123">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="8f608-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f608-124">備註</span><span class="sxs-lookup"><span data-stu-id="8f608-124">Remarks</span></span>  

 <span data-ttu-id="8f608-125">針對計算簽章的 `wszFilePath` 大小而不建立簽章，請指定 null。</span><span class="sxs-lookup"><span data-stu-id="8f608-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="8f608-126">簽章可以直接儲存在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8f608-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f608-127">需求</span><span class="sxs-lookup"><span data-stu-id="8f608-127">Requirements</span></span>  

 <span data-ttu-id="8f608-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f608-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f608-129">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="8f608-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8f608-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8f608-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f608-131">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f608-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f608-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f608-132">See also</span></span>

- [<span data-ttu-id="8f608-133">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="8f608-133">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="8f608-134">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8f608-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
