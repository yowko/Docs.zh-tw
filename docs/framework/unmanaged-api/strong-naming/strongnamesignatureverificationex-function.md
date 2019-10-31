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
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121151"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="8823c-102">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="8823c-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="8823c-103">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="8823c-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="8823c-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="8823c-104">This function has been deprecated.</span></span> <span data-ttu-id="8823c-105">請改用[ICLRStrongName：： StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8823c-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8823c-106">語法</span><span class="sxs-lookup"><span data-stu-id="8823c-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8823c-107">參數</span><span class="sxs-lookup"><span data-stu-id="8823c-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8823c-108">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="8823c-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="8823c-109">[in] `true` 執行驗證，即使需要覆寫登錄設定也一樣。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="8823c-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="8823c-110">[out] `true` 是否已驗證強式名稱簽章;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="8823c-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="8823c-111">如果驗證因為登錄設定而成功，`pfWasVerified` 也會設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8823c-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8823c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="8823c-112">Return Value</span></span>  
 <span data-ttu-id="8823c-113">如果驗證成功，則 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="8823c-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8823c-114">備註</span><span class="sxs-lookup"><span data-stu-id="8823c-114">Remarks</span></span>  
 <span data-ttu-id="8823c-115">`StrongNameSignatureVerificationEx` 提供類似[StrongNameSignatureVerification](strongnamesignatureverification-function.md)函數的功能。</span><span class="sxs-lookup"><span data-stu-id="8823c-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="8823c-116">不過，`StrongNameSignatureVerificationEx` 的第二個輸入參數和輸出參數是 `BOOLEAN` 類型，而不是 `DWORD`。</span><span class="sxs-lookup"><span data-stu-id="8823c-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8823c-117">需求</span><span class="sxs-lookup"><span data-stu-id="8823c-117">Requirements</span></span>  
 <span data-ttu-id="8823c-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8823c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8823c-119">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="8823c-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8823c-120">連結**庫：** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8823c-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="8823c-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8823c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8823c-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="8823c-122">See also</span></span>

- [<span data-ttu-id="8823c-123">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="8823c-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="8823c-124">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="8823c-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="8823c-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8823c-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
