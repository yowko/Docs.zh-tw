---
title: "ICLRStrongName::StrongNameSignatureGenerationEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247bcfa3c9f7a02dea331ff14948a00812fb06e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="9eab8-102">ICLRStrongName::StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="9eab8-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="9eab8-103">產生強式名稱簽章的指定組件中，根據指定的旗標。</span><span class="sxs-lookup"><span data-stu-id="9eab8-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eab8-104">語法</span><span class="sxs-lookup"><span data-stu-id="9eab8-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9eab8-105">參數</span><span class="sxs-lookup"><span data-stu-id="9eab8-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9eab8-106">[in]包含產生強式名稱簽章的組件資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9eab8-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="9eab8-107">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="9eab8-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="9eab8-108">如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="9eab8-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9eab8-109">在此情況下，儲存在容器中的金鑰組用來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="9eab8-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="9eab8-110">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="9eab8-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9eab8-111">[in]公開/私密金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="9eab8-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9eab8-112">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="9eab8-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9eab8-113">如果`pbKeyBlob`是 null，所指定的金鑰容器`wszKeyContainer`假設為包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9eab8-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9eab8-114">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="9eab8-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="9eab8-115">[out]Common language runtime 會回到此處簽章的位置指標。</span><span class="sxs-lookup"><span data-stu-id="9eab8-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="9eab8-116">如果`ppbSignatureBlob`是 null，執行階段會儲存簽章中所指定的檔案`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="9eab8-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="9eab8-117">如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，以傳回簽章。</span><span class="sxs-lookup"><span data-stu-id="9eab8-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="9eab8-118">呼叫端必須釋放此空間使用[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9eab8-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="9eab8-119">[out]大小，以位元組為單位傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="9eab8-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9eab8-120">[in]一或多個下列值：</span><span class="sxs-lookup"><span data-stu-id="9eab8-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="9eab8-121">`SN_SIGN_ALL_FILES`(0x00000001)-重新整理所有連結模組雜湊。</span><span class="sxs-lookup"><span data-stu-id="9eab8-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="9eab8-122">`SN_TEST_SIGN`(0x00000002)-測試簽署組件。</span><span class="sxs-lookup"><span data-stu-id="9eab8-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9eab8-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="9eab8-123">Return Value</span></span>  
 <span data-ttu-id="9eab8-124">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="9eab8-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eab8-125">備註</span><span class="sxs-lookup"><span data-stu-id="9eab8-125">Remarks</span></span>  
 <span data-ttu-id="9eab8-126">指定 null`wszFilePath`計算簽章的大小，而不需要建立簽章。</span><span class="sxs-lookup"><span data-stu-id="9eab8-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="9eab8-127">簽章可以直接儲存在檔案中，或傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="9eab8-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="9eab8-128">如果`SN_SIGN_ALL_FILES`指定，但不包含公開金鑰 (兩者`pbKeyBlob`和`wszFilePath`都是 null)，連結模組的雜湊都會重新計算，但不重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="9eab8-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="9eab8-129">如果`SN_TEST_SIGN`指定，則表示組件已簽署為強式名稱不會修改通用語言執行階段標頭。</span><span class="sxs-lookup"><span data-stu-id="9eab8-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eab8-130">需求</span><span class="sxs-lookup"><span data-stu-id="9eab8-130">Requirements</span></span>  
 <span data-ttu-id="9eab8-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9eab8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eab8-132">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9eab8-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9eab8-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9eab8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9eab8-134">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eab8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eab8-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="9eab8-135">See Also</span></span>  
 [<span data-ttu-id="9eab8-136">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="9eab8-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="9eab8-137">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="9eab8-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
