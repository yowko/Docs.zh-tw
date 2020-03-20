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
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176899"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="d8aa9-102">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="d8aa9-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="d8aa9-103">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="d8aa9-104">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-104">This function has been deprecated.</span></span> <span data-ttu-id="d8aa9-105">改用[ICLR 強式名稱：：強式名稱簽名生成](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8aa9-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8aa9-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d8aa9-107">參數</span><span class="sxs-lookup"><span data-stu-id="d8aa9-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d8aa9-108">[在]包含將為其生成強式名稱簽名的組件資訊清單的檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="d8aa9-109">[在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="d8aa9-110">如果`pbKeyBlob`為 null，`wszKeyContainer`則必須在加密服務提供者 （CSP） 中指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="d8aa9-111">在這種情況下，存儲在容器中的金鑰組用於對檔進行簽名。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="d8aa9-112">如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="d8aa9-113">金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="d8aa9-114">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d8aa9-115">[在]指向公開金鑰/私密金鑰對的指標。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d8aa9-116">此對採用 Win32`CryptExportKey`函數創建的格式。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d8aa9-117">如果`pbKeyBlob`為 null，則假定 指定的`wszKeyContainer`鍵容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d8aa9-118">[在]的大小（以位元組為單位）的大小`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="d8aa9-119">[出]指向公共語言運行時返回簽名的位置的指標。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="d8aa9-120">如果`ppbSignatureBlob`為 null，運行時將簽名存儲在 指定的`wszFilePath`檔中。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="d8aa9-121">如果`ppbSignatureBlob`為 null，則通用語言運行時會分配用於返回簽名的空間。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="d8aa9-122">調用方必須使用[強式名稱自由緩衝區](strongnamefreebuffer-function.md)函數釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="d8aa9-123">[出]返回的簽名的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8aa9-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8aa9-124">Return Value</span></span>  
 <span data-ttu-id="d8aa9-125">`true`成功完成;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="d8aa9-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8aa9-126">備註</span><span class="sxs-lookup"><span data-stu-id="d8aa9-126">Remarks</span></span>  
 <span data-ttu-id="d8aa9-127">指定 null`wszFilePath`以計算簽名的大小而不創建簽名。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="d8aa9-128">簽名可以直接存儲在檔中，也可以返回到調用方。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="d8aa9-129">如果`StrongNameSignatureGeneration`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8aa9-130">需求</span><span class="sxs-lookup"><span data-stu-id="d8aa9-130">Requirements</span></span>  
 <span data-ttu-id="d8aa9-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8aa9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8aa9-132">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="d8aa9-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d8aa9-133">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d8aa9-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8aa9-134">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8aa9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8aa9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8aa9-135">See also</span></span>

- [<span data-ttu-id="d8aa9-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="d8aa9-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="d8aa9-137">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="d8aa9-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="d8aa9-138">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d8aa9-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
