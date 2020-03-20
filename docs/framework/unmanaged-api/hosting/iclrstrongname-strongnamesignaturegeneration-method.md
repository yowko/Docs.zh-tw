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
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178045"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="3dd87-102">ICLRStrongName::StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="3dd87-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="3dd87-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="3dd87-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd87-104">語法</span><span class="sxs-lookup"><span data-stu-id="3dd87-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3dd87-105">參數</span><span class="sxs-lookup"><span data-stu-id="3dd87-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3dd87-106">[在]包含將為其生成強式名稱簽名的組件資訊清單的檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="3dd87-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="3dd87-107">[在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3dd87-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="3dd87-108">如果`pbKeyBlob`為 null，`wszKeyContainer`則必須在加密服務提供者 （CSP） 中指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="3dd87-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="3dd87-109">在這種情況下，存儲在容器中的金鑰組用於對檔進行簽名。</span><span class="sxs-lookup"><span data-stu-id="3dd87-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="3dd87-110">如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。</span><span class="sxs-lookup"><span data-stu-id="3dd87-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="3dd87-111">金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。</span><span class="sxs-lookup"><span data-stu-id="3dd87-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="3dd87-112">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="3dd87-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="3dd87-113">[在]指向公開金鑰/私密金鑰對的指標。</span><span class="sxs-lookup"><span data-stu-id="3dd87-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="3dd87-114">此對採用 Win32`CryptExportKey`函數創建的格式。</span><span class="sxs-lookup"><span data-stu-id="3dd87-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="3dd87-115">如果`pbKeyBlob`為 null，則假定 指定的`wszKeyContainer`鍵容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="3dd87-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="3dd87-116">[在]的大小（以位元組為單位）的大小`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="3dd87-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="3dd87-117">[出]指向公共語言運行時返回簽名的位置的指標。</span><span class="sxs-lookup"><span data-stu-id="3dd87-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="3dd87-118">如果`ppbSignatureBlob`為 null，運行時將簽名存儲在 指定的`wszFilePath`檔中。</span><span class="sxs-lookup"><span data-stu-id="3dd87-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="3dd87-119">如果`ppbSignatureBlob`為 null，則通用語言運行時會分配用於返回簽名的空間。</span><span class="sxs-lookup"><span data-stu-id="3dd87-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="3dd87-120">調用方必須使用[ICLRStrongNameName：：StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="3dd87-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="3dd87-121">[出]返回的簽名的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3dd87-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dd87-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="3dd87-122">Return Value</span></span>  
 <span data-ttu-id="3dd87-123">`S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="3dd87-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd87-124">備註</span><span class="sxs-lookup"><span data-stu-id="3dd87-124">Remarks</span></span>  
 <span data-ttu-id="3dd87-125">指定 null`wszFilePath`以計算簽名的大小而不創建簽名。</span><span class="sxs-lookup"><span data-stu-id="3dd87-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="3dd87-126">簽名可以直接存儲在檔中，也可以返回到調用方。</span><span class="sxs-lookup"><span data-stu-id="3dd87-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd87-127">需求</span><span class="sxs-lookup"><span data-stu-id="3dd87-127">Requirements</span></span>  
 <span data-ttu-id="3dd87-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3dd87-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd87-129">**標題：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3dd87-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3dd87-130">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3dd87-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dd87-131">**.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd87-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd87-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dd87-132">See also</span></span>

- [<span data-ttu-id="3dd87-133">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="3dd87-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="3dd87-134">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="3dd87-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
