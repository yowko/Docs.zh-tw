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
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798974"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="bedab-102">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="bedab-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="bedab-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="bedab-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="bedab-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="bedab-104">This function has been deprecated.</span></span> <span data-ttu-id="bedab-105">請改用[ICLRStrongName：： StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="bedab-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bedab-106">語法</span><span class="sxs-lookup"><span data-stu-id="bedab-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bedab-107">參數</span><span class="sxs-lookup"><span data-stu-id="bedab-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="bedab-108">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="bedab-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="bedab-109">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="bedab-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="bedab-110">如果`pbKeyBlob`為 null， `wszKeyContainer`必須在密碼編譯服務提供者（CSP）內指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="bedab-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="bedab-111">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="bedab-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="bedab-112">如果`pbKeyBlob`不是 null，則會假設金鑰組包含在金鑰二進位大型物件（BLOB）中。</span><span class="sxs-lookup"><span data-stu-id="bedab-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="bedab-113">金鑰必須是 1024-bit Rivest-Shamir-Adleman （RSA）簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="bedab-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="bedab-114">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="bedab-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="bedab-115">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="bedab-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="bedab-116">這組會使用 Win32 `CryptExportKey`函式所建立的格式。</span><span class="sxs-lookup"><span data-stu-id="bedab-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="bedab-117">如果`pbKeyBlob`為 null，則`wszKeyContainer`會假設指定的金鑰容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="bedab-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="bedab-118">在的大小（以位元組為單位`pbKeyBlob`）。</span><span class="sxs-lookup"><span data-stu-id="bedab-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="bedab-119">脫銷通用語言執行時間傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="bedab-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="bedab-120">如果`ppbSignatureBlob`為 null，則執行時間會將簽章儲存在所`wszFilePath`指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="bedab-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="bedab-121">如果`ppbSignatureBlob`不是 null，通用語言執行時間會配置用來傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="bedab-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="bedab-122">呼叫端必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="bedab-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="bedab-123">脫銷所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="bedab-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bedab-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="bedab-124">Return Value</span></span>  
 <span data-ttu-id="bedab-125">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="bedab-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bedab-126">備註</span><span class="sxs-lookup"><span data-stu-id="bedab-126">Remarks</span></span>  
 <span data-ttu-id="bedab-127">針對`wszFilePath`指定 null 以計算簽章的大小，而不建立簽章。</span><span class="sxs-lookup"><span data-stu-id="bedab-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="bedab-128">簽章可以直接儲存在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="bedab-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="bedab-129">如果 `StrongNameSignatureGeneration` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bedab-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bedab-130">需求</span><span class="sxs-lookup"><span data-stu-id="bedab-130">Requirements</span></span>  
 <span data-ttu-id="bedab-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bedab-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bedab-132">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="bedab-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bedab-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bedab-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bedab-134">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bedab-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedab-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bedab-135">See also</span></span>

- [<span data-ttu-id="bedab-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="bedab-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="bedab-137">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="bedab-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="bedab-138">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="bedab-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
