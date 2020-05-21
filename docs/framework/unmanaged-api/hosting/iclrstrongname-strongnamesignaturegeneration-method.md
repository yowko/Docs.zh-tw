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
ms.openlocfilehash: a8c9eab719f6a4f233490e544f67cf779ea10b20
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763029"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="458b9-102">ICLRStrongName::StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="458b9-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="458b9-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="458b9-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="458b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="458b9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="458b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="458b9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="458b9-106">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="458b9-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="458b9-107">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="458b9-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="458b9-108">如果 `pbKeyBlob` 為 null， `wszKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="458b9-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="458b9-109">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="458b9-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="458b9-110">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="458b9-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="458b9-111">金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="458b9-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="458b9-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="458b9-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="458b9-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="458b9-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="458b9-114">這組會使用 Win32 函式所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="458b9-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="458b9-115">如果 `pbKeyBlob` 為 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="458b9-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="458b9-116">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="458b9-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="458b9-117">脫銷通用語言執行時間傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="458b9-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="458b9-118">如果 `ppbSignatureBlob` 為 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="458b9-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="458b9-119">如果不 `ppbSignatureBlob` 是 null，通用語言執行時間會配置用來傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="458b9-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="458b9-120">呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="458b9-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="458b9-121">脫銷所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="458b9-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="458b9-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="458b9-122">Return Value</span></span>  
 <span data-ttu-id="458b9-123">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="458b9-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="458b9-124">備註</span><span class="sxs-lookup"><span data-stu-id="458b9-124">Remarks</span></span>  
 <span data-ttu-id="458b9-125">針對指定 null `wszFilePath` 以計算簽章的大小，而不建立簽章。</span><span class="sxs-lookup"><span data-stu-id="458b9-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="458b9-126">簽章可以直接儲存在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="458b9-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458b9-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="458b9-127">Requirements</span></span>  
 <span data-ttu-id="458b9-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="458b9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458b9-129">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="458b9-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="458b9-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="458b9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="458b9-131">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458b9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458b9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="458b9-132">See also</span></span>

- [<span data-ttu-id="458b9-133">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="458b9-133">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="458b9-134">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="458b9-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
