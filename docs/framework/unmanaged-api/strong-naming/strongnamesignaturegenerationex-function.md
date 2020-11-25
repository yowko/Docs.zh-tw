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
ms.openlocfilehash: 96dae519d73505a30c8593e9883da7338525ea2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708513"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="9d9a4-102">StrongNameSignatureGenerationEx 函式</span><span class="sxs-lookup"><span data-stu-id="9d9a4-102">StrongNameSignatureGenerationEx Function</span></span>

<span data-ttu-id="9d9a4-103">根據指定的旗標，產生指定元件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="9d9a4-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-104">This function has been deprecated.</span></span> <span data-ttu-id="9d9a4-105">請改用 [ICLRStrongName：： StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d9a4-106">語法</span><span class="sxs-lookup"><span data-stu-id="9d9a4-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9d9a4-107">參數</span><span class="sxs-lookup"><span data-stu-id="9d9a4-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9d9a4-108">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="9d9a4-109">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="9d9a4-110">如果 `pbKeyBlob` 是 null，則 `wszKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9d9a4-111">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="9d9a4-112">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9d9a4-113">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9d9a4-114">此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9d9a4-115">如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9d9a4-116">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="9d9a4-117">擴展Common language runtime 傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="9d9a4-118">如果 `ppbSignatureBlob` 是 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="9d9a4-119">如果不 `ppbSignatureBlob` 是 null，則 common language runtime 會配置要傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="9d9a4-120">呼叫端必須使用 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函式釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="9d9a4-121">擴展所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d9a4-122">在下列一個或多個值：</span><span class="sxs-lookup"><span data-stu-id="9d9a4-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="9d9a4-123">`SN_SIGN_ALL_FILES` (0x00000001) -重新計算連結模組的所有雜湊。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="9d9a4-124">`SN_TEST_SIGN` (0x00000002) -測試簽署元件。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d9a4-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d9a4-125">Return Value</span></span>  

 <span data-ttu-id="9d9a4-126">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d9a4-127">備註</span><span class="sxs-lookup"><span data-stu-id="9d9a4-127">Remarks</span></span>  

 <span data-ttu-id="9d9a4-128">針對計算簽章的 `wszFilePath` 大小而不建立簽章，請指定 null。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="9d9a4-129">簽章可以直接儲存在檔案中，也可以傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="9d9a4-130">如果 `SN_SIGN_ALL_FILES` 指定了，但未包含公開金鑰 (則 `pbKeyBlob` 和都是 `wszFilePath` null) ，則會重新計算連結模組的雜湊，但不會重新簽署元件。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="9d9a4-131">如果 `SN_TEST_SIGN` 指定了，就不會修改 common language runtime 標頭，以表示元件是以強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="9d9a4-132">如果函式 `StrongNameSignatureGenerationEx` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d9a4-133">需求</span><span class="sxs-lookup"><span data-stu-id="9d9a4-133">Requirements</span></span>  

 <span data-ttu-id="9d9a4-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9a4-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d9a4-135">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="9d9a4-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9d9a4-136">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9d9a4-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d9a4-137">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d9a4-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9a4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d9a4-138">See also</span></span>

- [<span data-ttu-id="9d9a4-139">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="9d9a4-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="9d9a4-140">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="9d9a4-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="9d9a4-141">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="9d9a4-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
