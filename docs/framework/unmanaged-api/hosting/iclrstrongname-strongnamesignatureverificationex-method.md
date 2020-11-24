---
title: ICLRStrongName::StrongNameSignatureVerificationEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: 9caeb72c57260012ae2b459950bf19d907da1d98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671547"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="ae942-102">ICLRStrongName::StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="ae942-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>

<span data-ttu-id="ae942-103">取得值，這個值會指出所提供路徑的組件資訊清單是否包含強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="ae942-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae942-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae942-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae942-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae942-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="ae942-106">在可攜式可執行檔的路徑 ( .exe 或 .dll) 檔，以供要驗證的元件。</span><span class="sxs-lookup"><span data-stu-id="ae942-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="ae942-107">[in] `true` 即使需要覆寫登錄設定，還是要執行驗證;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ae942-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="ae942-108">[out] `true` 如果已驗證強式名稱簽章，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ae942-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="ae942-109">`pfWasVerified``false`如果驗證因為登錄設定而成功，則也會設定為。</span><span class="sxs-lookup"><span data-stu-id="ae942-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae942-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae942-110">Return Value</span></span>  

 <span data-ttu-id="ae942-111">`S_OK` 如果驗證成功，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="ae942-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae942-112">備註</span><span class="sxs-lookup"><span data-stu-id="ae942-112">Remarks</span></span>  

 <span data-ttu-id="ae942-113">[ICLRStrongName：： StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md)方法提供的功能類似于[ICLRStrongName：： StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ae942-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="ae942-114">但是， [ICLRStrongName：： StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) 的第二個輸入參數和 output 參數的類型， `BOOLEAN` 而不是 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="ae942-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae942-115">需求</span><span class="sxs-lookup"><span data-stu-id="ae942-115">Requirements</span></span>  

 <span data-ttu-id="ae942-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae942-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae942-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="ae942-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ae942-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ae942-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae942-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae942-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae942-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae942-120">See also</span></span>

- [<span data-ttu-id="ae942-121">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="ae942-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="ae942-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ae942-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
