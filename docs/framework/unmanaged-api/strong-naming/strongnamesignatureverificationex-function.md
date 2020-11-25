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
ms.openlocfilehash: 27417c379411e242c48d6d9b0c99de833f7ede8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719264"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="7f5d0-102">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="7f5d0-102">StrongNameSignatureVerificationEx Function</span></span>

<span data-ttu-id="7f5d0-103">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="7f5d0-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-104">This function has been deprecated.</span></span> <span data-ttu-id="7f5d0-105">請改用 [ICLRStrongName：： StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5d0-106">語法</span><span class="sxs-lookup"><span data-stu-id="7f5d0-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f5d0-107">參數</span><span class="sxs-lookup"><span data-stu-id="7f5d0-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="7f5d0-108">在可攜式可執行檔的路徑 ( .exe 或 .dll) 檔，以供要驗證的元件。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="7f5d0-109">[in] `true` 即使需要覆寫登錄設定，還是要執行驗證;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="7f5d0-110">[out] `true` 如果已驗證強式名稱簽章，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="7f5d0-111">`pfWasVerified``false`如果驗證因為登錄設定而成功，則也會設定為。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f5d0-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7f5d0-112">Return Value</span></span>  

 <span data-ttu-id="7f5d0-113">`true` 如果驗證成功，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f5d0-114">備註</span><span class="sxs-lookup"><span data-stu-id="7f5d0-114">Remarks</span></span>  

 <span data-ttu-id="7f5d0-115">`StrongNameSignatureVerificationEx` 提供類似于 [StrongNameSignatureVerification](strongnamesignatureverification-function.md) 函數的功能。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="7f5d0-116">但是，的第二個輸入參數和的輸出參數 `StrongNameSignatureVerificationEx` 是類型， `BOOLEAN` 而不是 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f5d0-117">需求</span><span class="sxs-lookup"><span data-stu-id="7f5d0-117">Requirements</span></span>  

 <span data-ttu-id="7f5d0-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f5d0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5d0-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="7f5d0-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7f5d0-120">連結 **庫：** 以資源的形式包含在 mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="7f5d0-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="7f5d0-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5d0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5d0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5d0-122">See also</span></span>

- [<span data-ttu-id="7f5d0-123">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="7f5d0-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="7f5d0-124">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="7f5d0-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="7f5d0-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="7f5d0-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
