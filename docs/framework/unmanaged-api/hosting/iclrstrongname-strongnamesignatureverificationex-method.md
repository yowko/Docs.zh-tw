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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad25603f5acd32aa21192f86364976eb93d23540
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717541"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="6283b-102">ICLRStrongName::StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="6283b-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="6283b-103">取得值，指出是否提供之路徑上的組件資訊清單包含強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="6283b-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6283b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6283b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6283b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6283b-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6283b-106">[in]可攜式可執行檔 （.exe 或.dll） 檔來進行驗證的組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6283b-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="6283b-107">[in]`true`進行驗證，即使它是必要的登錄設定會覆寫，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="6283b-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="6283b-108">[out]`true`強式名稱簽章是否已驗證，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="6283b-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="6283b-109">`pfWasVerified` 也會設定為`false`若驗證成功因登錄設定。</span><span class="sxs-lookup"><span data-stu-id="6283b-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6283b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6283b-110">Return Value</span></span>  
 <span data-ttu-id="6283b-111">`S_OK` 如果驗證成功;否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="6283b-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6283b-112">備註</span><span class="sxs-lookup"><span data-stu-id="6283b-112">Remarks</span></span>  
 <span data-ttu-id="6283b-113">[Iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)方法會提供功能類似[iclrstrongname:: Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="6283b-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="6283b-114">不過，第二個輸入參數和輸出參數[iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)的型別`BOOLEAN`而不是`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="6283b-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6283b-115">需求</span><span class="sxs-lookup"><span data-stu-id="6283b-115">Requirements</span></span>  
 <span data-ttu-id="6283b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6283b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6283b-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6283b-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6283b-118">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6283b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6283b-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6283b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6283b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6283b-120">See also</span></span>
- [<span data-ttu-id="6283b-121">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="6283b-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="6283b-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="6283b-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
