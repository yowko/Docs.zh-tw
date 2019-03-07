---
title: StrongNameSignatureVerificationEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3f9dbbdf7ff560f292fed327a2ca1dd26c29a19
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491889"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="3c90b-102">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="3c90b-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="3c90b-103">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="3c90b-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="3c90b-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="3c90b-104">This function has been deprecated.</span></span> <span data-ttu-id="3c90b-105">使用[iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="3c90b-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c90b-106">語法</span><span class="sxs-lookup"><span data-stu-id="3c90b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c90b-107">參數</span><span class="sxs-lookup"><span data-stu-id="3c90b-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3c90b-108">[in]可攜式可執行檔 （.exe 或.dll） 檔來進行驗證的組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="3c90b-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="3c90b-109">[in]`true`進行驗證，即使它是必要的登錄設定會覆寫，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="3c90b-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="3c90b-110">[out]`true`強式名稱簽章是否已驗證，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="3c90b-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="3c90b-111">`pfWasVerified` 也會設定為`false`若驗證成功因登錄設定。</span><span class="sxs-lookup"><span data-stu-id="3c90b-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c90b-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c90b-112">Return Value</span></span>  
 <span data-ttu-id="3c90b-113">`true` 如果驗證成功;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="3c90b-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c90b-114">備註</span><span class="sxs-lookup"><span data-stu-id="3c90b-114">Remarks</span></span>  
 <span data-ttu-id="3c90b-115">`StrongNameSignatureVerificationEx` 提供的功能類似於[StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="3c90b-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="3c90b-116">不過，第二個輸入參數和輸出參數`StrongNameSignatureVerificationEx`屬於類型`BOOLEAN`而不是`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="3c90b-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c90b-117">需求</span><span class="sxs-lookup"><span data-stu-id="3c90b-117">Requirements</span></span>  
 <span data-ttu-id="3c90b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c90b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c90b-119">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3c90b-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3c90b-120">**程式庫：** 包含做為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3c90b-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3c90b-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c90b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c90b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c90b-122">See also</span></span>
- [<span data-ttu-id="3c90b-123">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="3c90b-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="3c90b-124">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="3c90b-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="3c90b-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="3c90b-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
