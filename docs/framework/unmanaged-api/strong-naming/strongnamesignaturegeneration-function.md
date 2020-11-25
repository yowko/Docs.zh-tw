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
ms.openlocfilehash: 78a89c07b9a7ddbccee9716de37c96d23635f87b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708521"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="1f02e-102">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="1f02e-102">StrongNameSignatureGeneration Function</span></span>

<span data-ttu-id="1f02e-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="1f02e-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="1f02e-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="1f02e-104">This function has been deprecated.</span></span> <span data-ttu-id="1f02e-105">請改用 [ICLRStrongName：： StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="1f02e-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f02e-106">語法</span><span class="sxs-lookup"><span data-stu-id="1f02e-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1f02e-107">參數</span><span class="sxs-lookup"><span data-stu-id="1f02e-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="1f02e-108">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="1f02e-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="1f02e-109">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1f02e-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="1f02e-110">如果 `pbKeyBlob` 是 null，則 `wszKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。</span><span class="sxs-lookup"><span data-stu-id="1f02e-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="1f02e-111">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="1f02e-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="1f02e-112">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。</span><span class="sxs-lookup"><span data-stu-id="1f02e-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="1f02e-113">金鑰必須是 1024-bit Rivest-Shamir-Adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="1f02e-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="1f02e-114">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="1f02e-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1f02e-115">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="1f02e-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1f02e-116">此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="1f02e-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1f02e-117">如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1f02e-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1f02e-118">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="1f02e-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="1f02e-119">擴展Common language runtime 傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="1f02e-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="1f02e-120">如果 `ppbSignatureBlob` 是 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="1f02e-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="1f02e-121">如果不 `ppbSignatureBlob` 是 null，則 common language runtime 會配置要傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="1f02e-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="1f02e-122">呼叫端必須使用 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函式釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="1f02e-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="1f02e-123">擴展所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1f02e-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f02e-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="1f02e-124">Return Value</span></span>  

 <span data-ttu-id="1f02e-125">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1f02e-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f02e-126">備註</span><span class="sxs-lookup"><span data-stu-id="1f02e-126">Remarks</span></span>  

 <span data-ttu-id="1f02e-127">針對計算簽章的 `wszFilePath` 大小而不建立簽章，請指定 null。</span><span class="sxs-lookup"><span data-stu-id="1f02e-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="1f02e-128">簽章可以直接儲存在檔案中，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="1f02e-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="1f02e-129">如果函式 `StrongNameSignatureGeneration` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f02e-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f02e-130">需求</span><span class="sxs-lookup"><span data-stu-id="1f02e-130">Requirements</span></span>  

 <span data-ttu-id="1f02e-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f02e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f02e-132">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="1f02e-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1f02e-133">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1f02e-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f02e-134">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f02e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f02e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f02e-135">See also</span></span>

- [<span data-ttu-id="1f02e-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="1f02e-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="1f02e-137">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="1f02e-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="1f02e-138">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1f02e-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
