---
title: "StrongNameGetPublicKey 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type: DLLExport
f1_keywords: StrongNameGetPublicKey
helpviewer_keywords: StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 243b5f8d94805d8631c7c79f424d9e6434213bb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="f4787-102">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="f4787-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="f4787-103">從私密/公開金鑰組取得的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f4787-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="f4787-104">密碼編譯服務提供者 (CSP) 內的金鑰容器名稱，或是為未經處理位元組的集合，您可以提供的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="f4787-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="f4787-105">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="f4787-105">This function has been deprecated.</span></span> <span data-ttu-id="f4787-106">使用[iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="f4787-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4787-107">語法</span><span class="sxs-lookup"><span data-stu-id="f4787-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4787-108">參數</span><span class="sxs-lookup"><span data-stu-id="f4787-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="f4787-109">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="f4787-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="f4787-110">如果`pbKeyBlob`為 null，`szKeyContainer`必須指定 CSP 內是有效的容器。</span><span class="sxs-lookup"><span data-stu-id="f4787-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="f4787-111">在此情況下，`StrongNameGetPublicKey`從儲存在容器中的金鑰組擷取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f4787-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="f4787-112">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="f4787-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f4787-113">索引鍵必須是 1024年位元用於 Rivest-shamir-adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="f4787-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f4787-114">此時會支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="f4787-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f4787-115">[in]公開/私密金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="f4787-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f4787-116">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="f4787-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f4787-117">如果`pbKeyBlob`是 null，所指定的金鑰容器`szKeyContainer`假設為包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="f4787-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f4787-118">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="f4787-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f4787-119">[out]傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="f4787-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="f4787-120">`ppbPublicKeyBlob`參數是由 common language runtime 配置並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="f4787-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="f4787-121">呼叫端必須釋放的記憶體使用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f4787-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f4787-122">[out]傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="f4787-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4787-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4787-123">Return Value</span></span>  
 <span data-ttu-id="f4787-124">`true`如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="f4787-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4787-125">備註</span><span class="sxs-lookup"><span data-stu-id="f4787-125">Remarks</span></span>  
 <span data-ttu-id="f4787-126">中包含公用金鑰[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="f4787-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="f4787-127">如果`StrongNameGetPublicKey`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4787-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4787-128">需求</span><span class="sxs-lookup"><span data-stu-id="f4787-128">Requirements</span></span>  
 <span data-ttu-id="f4787-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4787-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4787-130">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f4787-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f4787-131">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f4787-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4787-132">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4787-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4787-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4787-133">See Also</span></span>  
 [<span data-ttu-id="f4787-134">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="f4787-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="f4787-135">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="f4787-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="f4787-136">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f4787-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="f4787-137">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="f4787-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
