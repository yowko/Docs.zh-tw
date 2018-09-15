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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f1eb4236bab72caf4421342e1f54d6d2f32607
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647800"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="03306-102">ICLRStrongName::StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="03306-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="03306-103">指定的組件中，根據指定的旗標產生的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="03306-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03306-104">語法</span><span class="sxs-lookup"><span data-stu-id="03306-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="03306-105">參數</span><span class="sxs-lookup"><span data-stu-id="03306-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="03306-106">[in]包含產生的強式名稱簽章的組件資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="03306-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="03306-107">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="03306-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="03306-108">如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="03306-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="03306-109">在此情況下，儲存在容器中的金鑰組來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="03306-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="03306-110">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="03306-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="03306-111">[in]Public/private 金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="03306-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="03306-112">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="03306-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="03306-113">如果`pbKeyBlob`是 null，藉由指定之金鑰容器`wszKeyContainer`會假設包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="03306-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="03306-114">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="03306-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="03306-115">[out]Common language runtime 會傳回簽章的位置指標。</span><span class="sxs-lookup"><span data-stu-id="03306-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="03306-116">如果`ppbSignatureBlob`是 null，執行階段存放區簽章中所指定的檔案`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="03306-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="03306-117">如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，在其中傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="03306-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="03306-118">呼叫端必須使用此空間釋放[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="03306-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="03306-119">[out]大小，以位元組為單位傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="03306-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="03306-120">[in]一或多個下列值：</span><span class="sxs-lookup"><span data-stu-id="03306-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="03306-121">`SN_SIGN_ALL_FILES` (0x00000001)-重新計算所有的雜湊，連結的模組。</span><span class="sxs-lookup"><span data-stu-id="03306-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="03306-122">`SN_TEST_SIGN` (0x00000002)-測試-簽署組件。</span><span class="sxs-lookup"><span data-stu-id="03306-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03306-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="03306-123">Return Value</span></span>  
 <span data-ttu-id="03306-124">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="03306-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03306-125">備註</span><span class="sxs-lookup"><span data-stu-id="03306-125">Remarks</span></span>  
 <span data-ttu-id="03306-126">指定 null`wszFilePath`來計算簽章的大小，而不需建立簽章。</span><span class="sxs-lookup"><span data-stu-id="03306-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="03306-127">簽章可以直接儲存在該檔案，或傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="03306-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="03306-128">如果`SN_SIGN_ALL_FILES`指定但不包含公開金鑰 (兩者`pbKeyBlob`和`wszFilePath`都是 null)，會重新計算雜湊，連結的模組，但不重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="03306-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="03306-129">如果`SN_TEST_SIGN`指定時，通用語言執行階段標頭不會修改來表示，以強式名稱簽署組件。</span><span class="sxs-lookup"><span data-stu-id="03306-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03306-130">需求</span><span class="sxs-lookup"><span data-stu-id="03306-130">Requirements</span></span>  
 <span data-ttu-id="03306-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03306-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03306-132">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="03306-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03306-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="03306-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03306-134">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03306-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03306-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03306-135">See Also</span></span>  
 [<span data-ttu-id="03306-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="03306-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="03306-137">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="03306-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
