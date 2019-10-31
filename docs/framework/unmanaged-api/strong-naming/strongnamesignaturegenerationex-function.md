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
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141582"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="8de9b-102">StrongNameSignatureGenerationEx 函式</span><span class="sxs-lookup"><span data-stu-id="8de9b-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="8de9b-103">根據指定的旗標，產生指定元件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="8de9b-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="8de9b-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="8de9b-104">This function has been deprecated.</span></span> <span data-ttu-id="8de9b-105">請改用[ICLRStrongName：： StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8de9b-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de9b-106">語法</span><span class="sxs-lookup"><span data-stu-id="8de9b-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="8de9b-107">參數</span><span class="sxs-lookup"><span data-stu-id="8de9b-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8de9b-108">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="8de9b-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="8de9b-109">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="8de9b-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="8de9b-110">如果 `pbKeyBlob` 為 null，`wszKeyContainer` 必須在密碼編譯服務提供者（CSP）內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="8de9b-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="8de9b-111">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="8de9b-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="8de9b-112">如果 `pbKeyBlob` 不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="8de9b-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8de9b-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="8de9b-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8de9b-114">這組會使用 Win32 `CryptExportKey` 函式所建立的格式。</span><span class="sxs-lookup"><span data-stu-id="8de9b-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8de9b-115">如果 `pbKeyBlob` 是 null，則會假設 `wszKeyContainer` 指定的金鑰容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="8de9b-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8de9b-116">在`pbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8de9b-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="8de9b-117">脫銷通用語言執行時間傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="8de9b-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="8de9b-118">如果 `ppbSignatureBlob` 為 null，執行時間會將簽章儲存在 `wszFilePath`所指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="8de9b-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="8de9b-119">如果 `ppbSignatureBlob` 不是 null，通用語言執行時間會配置用來傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="8de9b-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="8de9b-120">呼叫端必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="8de9b-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="8de9b-121">脫銷所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8de9b-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8de9b-122">在下列一個或多個值：</span><span class="sxs-lookup"><span data-stu-id="8de9b-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="8de9b-123">`SN_SIGN_ALL_FILES` （0x00000001）-重新計算連結模組的所有雜湊。</span><span class="sxs-lookup"><span data-stu-id="8de9b-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="8de9b-124">`SN_TEST_SIGN` （0x00000002）-測試-簽署元件。</span><span class="sxs-lookup"><span data-stu-id="8de9b-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8de9b-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="8de9b-125">Return Value</span></span>  
 <span data-ttu-id="8de9b-126">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="8de9b-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de9b-127">備註</span><span class="sxs-lookup"><span data-stu-id="8de9b-127">Remarks</span></span>  
 <span data-ttu-id="8de9b-128">為 `wszFilePath` 指定 null 以計算簽章的大小，而不建立簽章。</span><span class="sxs-lookup"><span data-stu-id="8de9b-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="8de9b-129">簽章可以直接儲存在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8de9b-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="8de9b-130">如果指定了 `SN_SIGN_ALL_FILES`，但不包含公開金鑰（`pbKeyBlob` 和 `wszFilePath` 都是 null），則會重新計算連結模組的雜湊，但不會重新簽署元件。</span><span class="sxs-lookup"><span data-stu-id="8de9b-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="8de9b-131">如果指定了 `SN_TEST_SIGN`，則不會修改 common language runtime 標頭，以指出元件是以強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="8de9b-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="8de9b-132">如果 `StrongNameSignatureGenerationEx` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8de9b-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de9b-133">需求</span><span class="sxs-lookup"><span data-stu-id="8de9b-133">Requirements</span></span>  
 <span data-ttu-id="8de9b-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8de9b-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de9b-135">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="8de9b-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8de9b-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8de9b-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8de9b-137">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de9b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de9b-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="8de9b-138">See also</span></span>

- [<span data-ttu-id="8de9b-139">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="8de9b-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="8de9b-140">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="8de9b-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="8de9b-141">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8de9b-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
