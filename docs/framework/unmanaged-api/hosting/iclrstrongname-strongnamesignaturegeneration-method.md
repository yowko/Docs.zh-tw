---
title: ICLRStrongName::StrongNameSignatureGeneration 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 217b54a615d7c553e714ef87b3c2bb6a1919ae98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435371"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="a6b3a-102">ICLRStrongName::StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="a6b3a-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="a6b3a-103">產生強式名稱簽章的指定組件。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6b3a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6b3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6b3a-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a6b3a-106">[in]包含產生強式名稱簽章的組件資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="a6b3a-107">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="a6b3a-108">如果`pbKeyBlob`為 null，`wszKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="a6b3a-109">在此情況下，儲存在容器中的金鑰組用來簽署檔案。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="a6b3a-110">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a6b3a-111">索引鍵必須是 1024年位元用於 Rivest-shamir-adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a6b3a-112">此時會支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a6b3a-113">[in]公開/私密金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a6b3a-114">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a6b3a-115">如果`pbKeyBlob`是 null，所指定的金鑰容器`wszKeyContainer`假設為包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a6b3a-116">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="a6b3a-117">[out]Common language runtime 會回到此處簽章的位置指標。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="a6b3a-118">如果`ppbSignatureBlob`是 null，執行階段會儲存簽章中所指定的檔案`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="a6b3a-119">如果`ppbSignatureBlob`是不是 null，common language runtime 配置的空間，以傳回簽章。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="a6b3a-120">呼叫端必須使用釋放此空間[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="a6b3a-121">[out]大小，以位元組為單位傳回的簽章。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6b3a-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="a6b3a-122">Return Value</span></span>  
 <span data-ttu-id="a6b3a-123">`S_OK` 如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6b3a-124">備註</span><span class="sxs-lookup"><span data-stu-id="a6b3a-124">Remarks</span></span>  
 <span data-ttu-id="a6b3a-125">指定 null`wszFilePath`計算簽章的大小，而不需要建立簽章。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="a6b3a-126">簽章能夠直接存放在檔案中，或傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b3a-127">需求</span><span class="sxs-lookup"><span data-stu-id="a6b3a-127">Requirements</span></span>  
 <span data-ttu-id="a6b3a-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6b3a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6b3a-129">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a6b3a-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a6b3a-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a6b3a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6b3a-131">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6b3a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b3a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6b3a-132">See Also</span></span>  
 [<span data-ttu-id="a6b3a-133">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="a6b3a-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="a6b3a-134">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="a6b3a-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
