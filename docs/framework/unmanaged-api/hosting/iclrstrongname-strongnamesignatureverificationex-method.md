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
ms.openlocfilehash: 5bd985a6870ae6f4cc2302b6a11e8e139180d839
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503987"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="09bda-102">ICLRStrongName::StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="09bda-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="09bda-103">取得值，指出所提供路徑的組件資訊清單是否包含強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="09bda-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09bda-104">語法</span><span class="sxs-lookup"><span data-stu-id="09bda-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09bda-105">參數</span><span class="sxs-lookup"><span data-stu-id="09bda-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="09bda-106">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="09bda-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="09bda-107">[in] `true`若要執行驗證，即使需要覆寫登錄設定也一樣。否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="09bda-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="09bda-108">[out] `true`如果已驗證強式名稱簽章，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="09bda-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="09bda-109">`pfWasVerified``false`如果驗證因為登錄設定而成功，也會設定為。</span><span class="sxs-lookup"><span data-stu-id="09bda-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09bda-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="09bda-110">Return Value</span></span>  
 <span data-ttu-id="09bda-111">`S_OK`如果驗證成功，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="09bda-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09bda-112">備註</span><span class="sxs-lookup"><span data-stu-id="09bda-112">Remarks</span></span>  
 <span data-ttu-id="09bda-113">[ICLRStrongName：： StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md)方法提供的功能類似于[ICLRStrongName：： StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="09bda-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="09bda-114">不過， [ICLRStrongName：： StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md)的第二個輸入參數和 output 參數是類型， `BOOLEAN` 而不是 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="09bda-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09bda-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="09bda-115">Requirements</span></span>  
 <span data-ttu-id="09bda-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09bda-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09bda-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="09bda-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="09bda-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="09bda-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09bda-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09bda-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09bda-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09bda-120">See also</span></span>

- [<span data-ttu-id="09bda-121">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="09bda-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="09bda-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="09bda-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
