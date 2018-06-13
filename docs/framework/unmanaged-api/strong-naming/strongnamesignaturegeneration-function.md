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
ms.openlocfilehash: c0555299779aebc6cc37c3863e8b5504b357b262
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461489"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="504ce-102">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="504ce-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="504ce-103">產生強式名稱簽章的指定組件。</span><span class="sxs-lookup"><span data-stu-id="504ce-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="504ce-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="504ce-104">This function has been deprecated.</span></span> <span data-ttu-id="504ce-105">使用[iclrstrongname:: Strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="504ce-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504ce-106">語法</span><span class="sxs-lookup"><span data-stu-id="504ce-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="504ce-107">參數</span><span class="sxs-lookup"><span data-stu-id="504ce-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="504ce-108">[in]包含產生強式名稱簽章的組件資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="504ce-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="504ce-109">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="504ce-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="504ce-110">如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="504ce-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="504ce-111">在此情況下，儲存在容器中的金鑰組用來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="504ce-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="504ce-112">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="504ce-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="504ce-113">索引鍵必須是 1024年位元用於 Rivest-shamir-adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="504ce-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="504ce-114">此時會支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="504ce-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="504ce-115">[in]公開/私密金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="504ce-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="504ce-116">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="504ce-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="504ce-117">如果`pbKeyBlob`是 null，所指定的金鑰容器`wszKeyContainer`假設為包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="504ce-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="504ce-118">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="504ce-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="504ce-119">[out]Common language runtime 會回到此處簽章的位置指標。</span><span class="sxs-lookup"><span data-stu-id="504ce-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="504ce-120">如果`ppbSignatureBlob`是 null，執行階段會儲存簽章中所指定的檔案`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="504ce-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="504ce-121">如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，以傳回簽章。</span><span class="sxs-lookup"><span data-stu-id="504ce-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="504ce-122">呼叫端必須釋放此空間使用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="504ce-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="504ce-123">[out]大小，以位元組為單位傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="504ce-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="504ce-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="504ce-124">Return Value</span></span>  
 <span data-ttu-id="504ce-125">`true` 如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="504ce-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="504ce-126">備註</span><span class="sxs-lookup"><span data-stu-id="504ce-126">Remarks</span></span>  
 <span data-ttu-id="504ce-127">指定 null`wszFilePath`計算簽章的大小，而不需要建立簽章。</span><span class="sxs-lookup"><span data-stu-id="504ce-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="504ce-128">簽章能夠直接存放在檔案中，或傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="504ce-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="504ce-129">如果`StrongNameSignatureGeneration`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="504ce-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="504ce-130">需求</span><span class="sxs-lookup"><span data-stu-id="504ce-130">Requirements</span></span>  
 <span data-ttu-id="504ce-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="504ce-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="504ce-132">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="504ce-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="504ce-133">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="504ce-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="504ce-134">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="504ce-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="504ce-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="504ce-135">See Also</span></span>  
 [<span data-ttu-id="504ce-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="504ce-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="504ce-137">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="504ce-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="504ce-138">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="504ce-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
