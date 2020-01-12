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
ms.openlocfilehash: fbc9ea6aab9f0c3d9be95e6affcd04342ce4c5cc
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901080"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="8d277-102">ICLRStrongName::StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="8d277-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="8d277-103">取得值，指出所提供路徑的組件資訊清單是否包含強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="8d277-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d277-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d277-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d277-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d277-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="8d277-106">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="8d277-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="8d277-107">[in] `true` 執行驗證，即使需要覆寫登錄設定也一樣。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="8d277-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="8d277-108">[out] `true` 是否已驗證強式名稱簽章;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="8d277-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="8d277-109">如果驗證因為登錄設定而成功，`pfWasVerified` 也會設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8d277-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d277-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d277-110">Return Value</span></span>  
 <span data-ttu-id="8d277-111">如果驗證成功，則 `S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="8d277-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d277-112">備註</span><span class="sxs-lookup"><span data-stu-id="8d277-112">Remarks</span></span>  
 <span data-ttu-id="8d277-113">[ICLRStrongName：： StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法提供的功能類似于[ICLRStrongName：： StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8d277-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="8d277-114">不過， [ICLRStrongName：： StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)的第二個輸入參數和 output 參數是 `BOOLEAN` 類型，而不是 `DWORD`。</span><span class="sxs-lookup"><span data-stu-id="8d277-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d277-115">需求</span><span class="sxs-lookup"><span data-stu-id="8d277-115">Requirements</span></span>  
 <span data-ttu-id="8d277-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d277-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d277-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="8d277-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8d277-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d277-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d277-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d277-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d277-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d277-120">See also</span></span>

- [<span data-ttu-id="8d277-121">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="8d277-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="8d277-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8d277-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
