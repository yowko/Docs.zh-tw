---
title: ICLRStrongName::StrongNameSignatureGenerationEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 78cc043953e6288df136b43590831569d112afef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674511"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="7bb28-102">ICLRStrongName::StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="7bb28-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>

<span data-ttu-id="7bb28-103">根據指定的旗標，產生指定元件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="7bb28-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb28-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bb28-104">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb28-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bb28-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="7bb28-106">在檔案的路徑，該檔案包含將產生強式名稱簽章之元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="7bb28-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="7bb28-107">在包含公開/私密金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="7bb28-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="7bb28-108">如果 `pbKeyBlob` 是 null，則 `wszKeyContainer` 必須在密碼編譯服務提供者中指定有效的容器， (CSP) 。</span><span class="sxs-lookup"><span data-stu-id="7bb28-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="7bb28-109">在此情況下，會使用儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="7bb28-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="7bb28-110">如果不 `pbKeyBlob` 是 null，則會假設金鑰組包含在 (BLOB) 的金鑰二進位大型物件中。</span><span class="sxs-lookup"><span data-stu-id="7bb28-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7bb28-111">在公開/私密金鑰組的指標。</span><span class="sxs-lookup"><span data-stu-id="7bb28-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="7bb28-112">此配對的格式是 Win32 函數所建立的格式 `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="7bb28-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="7bb28-113">如果 `pbKeyBlob` 是 null，則會假設指定的金鑰容器 `wszKeyContainer` 包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="7bb28-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7bb28-114">在的大小（以位元組為單位） `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="7bb28-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="7bb28-115">擴展Common language runtime 傳回簽章之位置的指標。</span><span class="sxs-lookup"><span data-stu-id="7bb28-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="7bb28-116">如果 `ppbSignatureBlob` 是 null，則執行時間會將簽章儲存在所指定的檔案中 `wszFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="7bb28-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="7bb28-117">如果不 `ppbSignatureBlob` 是 null，則 common language runtime 會配置要傳回簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="7bb28-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="7bb28-118">呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放此空間。</span><span class="sxs-lookup"><span data-stu-id="7bb28-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="7bb28-119">擴展所傳回簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7bb28-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7bb28-120">在下列一個或多個值：</span><span class="sxs-lookup"><span data-stu-id="7bb28-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="7bb28-121">`SN_SIGN_ALL_FILES` (0x00000001) -重新計算連結模組的所有雜湊。</span><span class="sxs-lookup"><span data-stu-id="7bb28-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="7bb28-122">`SN_TEST_SIGN` (0x00000002) -測試簽署元件。</span><span class="sxs-lookup"><span data-stu-id="7bb28-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bb28-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bb28-123">Return Value</span></span>  

 <span data-ttu-id="7bb28-124">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="7bb28-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bb28-125">備註</span><span class="sxs-lookup"><span data-stu-id="7bb28-125">Remarks</span></span>  

 <span data-ttu-id="7bb28-126">針對計算簽章的 `wszFilePath` 大小而不建立簽章，請指定 null。</span><span class="sxs-lookup"><span data-stu-id="7bb28-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="7bb28-127">簽章可以直接儲存在檔案中，也可以傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7bb28-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="7bb28-128">如果 `SN_SIGN_ALL_FILES` 指定了，但未包含公開金鑰 (則 `pbKeyBlob` 和都是 `wszFilePath` null) ，則會重新計算連結模組的雜湊，但不會重新簽署元件。</span><span class="sxs-lookup"><span data-stu-id="7bb28-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="7bb28-129">如果 `SN_TEST_SIGN` 指定了，就不會修改 common language runtime 標頭，以表示元件是以強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="7bb28-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb28-130">需求</span><span class="sxs-lookup"><span data-stu-id="7bb28-130">Requirements</span></span>  

 <span data-ttu-id="7bb28-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bb28-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb28-132">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="7bb28-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7bb28-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7bb28-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb28-134">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb28-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb28-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bb28-135">See also</span></span>

- [<span data-ttu-id="7bb28-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="7bb28-136">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="7bb28-137">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="7bb28-137">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
