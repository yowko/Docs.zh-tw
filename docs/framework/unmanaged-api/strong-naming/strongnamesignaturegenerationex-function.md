---
title: StrongNameSignatureGenerationEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c63a586473128281843ec100905e63d381f1a3f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500927"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="2cb22-102">StrongNameSignatureGenerationEx 函式</span><span class="sxs-lookup"><span data-stu-id="2cb22-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="2cb22-103">指定的組件中，根據指定的旗標產生的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="2cb22-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="2cb22-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="2cb22-104">This function has been deprecated.</span></span> <span data-ttu-id="2cb22-105">使用[iclrstrongname:: Strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="2cb22-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb22-106">語法</span><span class="sxs-lookup"><span data-stu-id="2cb22-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cb22-107">參數</span><span class="sxs-lookup"><span data-stu-id="2cb22-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2cb22-108">[in]包含產生的強式名稱簽章的組件資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2cb22-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="2cb22-109">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="2cb22-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="2cb22-110">如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="2cb22-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="2cb22-111">在此情況下，儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="2cb22-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="2cb22-112">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="2cb22-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="2cb22-113">[in]Public/private 金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="2cb22-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="2cb22-114">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="2cb22-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="2cb22-115">如果`pbKeyBlob`是 null，藉由指定之金鑰容器`wszKeyContainer`會假設包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="2cb22-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="2cb22-116">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="2cb22-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="2cb22-117">[out]Common language runtime 會傳回簽章的位置指標。</span><span class="sxs-lookup"><span data-stu-id="2cb22-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="2cb22-118">如果`ppbSignatureBlob`是 null，執行階段存放區簽章中所指定的檔案`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="2cb22-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="2cb22-119">如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，在其中傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="2cb22-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="2cb22-120">呼叫端必須使用此空間釋放[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="2cb22-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="2cb22-121">[out]大小，以位元組為單位傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="2cb22-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2cb22-122">[in]一或多個下列值：</span><span class="sxs-lookup"><span data-stu-id="2cb22-122">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="2cb22-123">`SN_SIGN_ALL_FILES` (0x00000001)-重新計算所有的雜湊，連結的模組。</span><span class="sxs-lookup"><span data-stu-id="2cb22-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="2cb22-124">`SN_TEST_SIGN` (0x00000002)-測試-簽署組件。</span><span class="sxs-lookup"><span data-stu-id="2cb22-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cb22-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="2cb22-125">Return Value</span></span>  
 <span data-ttu-id="2cb22-126">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="2cb22-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb22-127">備註</span><span class="sxs-lookup"><span data-stu-id="2cb22-127">Remarks</span></span>  
 <span data-ttu-id="2cb22-128">指定 null`wszFilePath`來計算簽章的大小，而不需建立簽章。</span><span class="sxs-lookup"><span data-stu-id="2cb22-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="2cb22-129">簽章可以直接儲存在該檔案，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="2cb22-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="2cb22-130">如果`SN_SIGN_ALL_FILES`指定但不包含公開金鑰 (兩者`pbKeyBlob`和`wszFilePath`都是 null)，會重新計算雜湊，連結的模組，但不重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="2cb22-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="2cb22-131">如果`SN_TEST_SIGN`指定時，通用語言執行階段標頭不會修改來表示，以強式名稱簽署組件。</span><span class="sxs-lookup"><span data-stu-id="2cb22-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="2cb22-132">如果`StrongNameSignatureGenerationEx`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2cb22-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb22-133">需求</span><span class="sxs-lookup"><span data-stu-id="2cb22-133">Requirements</span></span>  
 <span data-ttu-id="2cb22-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cb22-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb22-135">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2cb22-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2cb22-136">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2cb22-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cb22-137">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb22-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb22-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cb22-138">See also</span></span>
- [<span data-ttu-id="2cb22-139">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="2cb22-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="2cb22-140">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="2cb22-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="2cb22-141">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="2cb22-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
