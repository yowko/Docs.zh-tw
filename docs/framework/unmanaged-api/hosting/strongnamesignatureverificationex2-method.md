---
title: StrongNameSignatureVerificationEx2 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3b697a0bb2f58258816ce4f8133009b26f54a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220587"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="7df8a-102">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="7df8a-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="7df8a-103">驗證強式名稱的組件中，簽章，並提供實際的索引鍵與 ECMA 索引鍵的對應。</span><span class="sxs-lookup"><span data-stu-id="7df8a-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7df8a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7df8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7df8a-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7df8a-106">[in]可攜式可執行檔 （.exe 或.dll） 檔來進行驗證的組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="7df8a-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="7df8a-107">[in]`true`進行驗證，即使它是必要的登錄設定會覆寫，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="7df8a-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="7df8a-108">[in]從實際的索引鍵的 ECMA 公開金鑰對應的指標，用來驗證。</span><span class="sxs-lookup"><span data-stu-id="7df8a-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="7df8a-109">[in]實際的 ECMA 公開金鑰長度。</span><span class="sxs-lookup"><span data-stu-id="7df8a-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="7df8a-110">[out]`true`強式名稱簽章是否已驗證，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="7df8a-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="7df8a-111">這個參數也會設定為`false`若驗證成功因登錄設定。</span><span class="sxs-lookup"><span data-stu-id="7df8a-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7df8a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7df8a-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="7df8a-113">如果驗證成功;否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="7df8a-113">if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7df8a-114">需求</span><span class="sxs-lookup"><span data-stu-id="7df8a-114">Requirements</span></span>  
 <span data-ttu-id="7df8a-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7df8a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df8a-116">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7df8a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7df8a-117">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7df8a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7df8a-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7df8a-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7df8a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df8a-119">See also</span></span>

- [<span data-ttu-id="7df8a-120">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="7df8a-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="7df8a-121">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="7df8a-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="7df8a-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="7df8a-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
