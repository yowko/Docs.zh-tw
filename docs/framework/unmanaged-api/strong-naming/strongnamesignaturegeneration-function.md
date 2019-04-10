---
title: StrongNameSignatureGeneration 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e7df65c28fad6fa79ec7a18d8511955330b2817
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227739"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="41e97-102">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="41e97-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="41e97-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="41e97-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="41e97-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="41e97-104">This function has been deprecated.</span></span> <span data-ttu-id="41e97-105">使用[iclrstrongname:: Strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="41e97-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e97-106">語法</span><span class="sxs-lookup"><span data-stu-id="41e97-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e97-107">參數</span><span class="sxs-lookup"><span data-stu-id="41e97-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="41e97-108">[in]包含產生的強式名稱簽章的組件資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="41e97-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="41e97-109">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="41e97-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="41e97-110">如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="41e97-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="41e97-111">在此情況下，儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="41e97-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="41e97-112">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="41e97-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="41e97-113">索引鍵必須是 1024年位元 Rivest-shamir-adleman/digital signature Standard (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="41e97-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="41e97-114">目前支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="41e97-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="41e97-115">[in]Public/private 金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="41e97-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="41e97-116">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="41e97-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="41e97-117">如果`pbKeyBlob`是 null，藉由指定之金鑰容器`wszKeyContainer`會假設包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="41e97-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="41e97-118">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="41e97-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="41e97-119">[out]Common language runtime 會傳回簽章的位置指標。</span><span class="sxs-lookup"><span data-stu-id="41e97-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="41e97-120">如果`ppbSignatureBlob`是 null，執行階段存放區簽章中所指定的檔案`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="41e97-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="41e97-121">如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，在其中傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="41e97-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="41e97-122">呼叫端必須使用此空間釋放[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="41e97-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="41e97-123">[out]大小，以位元組為單位傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="41e97-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41e97-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="41e97-124">Return Value</span></span>  
 `true` <span data-ttu-id="41e97-125">如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="41e97-125">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e97-126">備註</span><span class="sxs-lookup"><span data-stu-id="41e97-126">Remarks</span></span>  
 <span data-ttu-id="41e97-127">指定 null`wszFilePath`來計算簽章的大小，而不需建立簽章。</span><span class="sxs-lookup"><span data-stu-id="41e97-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="41e97-128">簽章可以是直接存放在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="41e97-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="41e97-129">如果`StrongNameSignatureGeneration`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="41e97-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e97-130">需求</span><span class="sxs-lookup"><span data-stu-id="41e97-130">Requirements</span></span>  
 <span data-ttu-id="41e97-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41e97-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e97-132">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="41e97-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="41e97-133">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41e97-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="41e97-134">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="41e97-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="41e97-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e97-135">See also</span></span>

- [<span data-ttu-id="41e97-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="41e97-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="41e97-137">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="41e97-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="41e97-138">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="41e97-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
