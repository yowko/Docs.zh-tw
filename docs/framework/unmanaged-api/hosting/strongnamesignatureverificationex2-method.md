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
ms.openlocfilehash: cf8d6b7e45c0012d223173c85a92fac4fb044c6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141407"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="d50ef-102">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="d50ef-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="d50ef-103">驗證強式名稱元件的簽章，並提供從 ECMA 金鑰到實際金鑰的對應。</span><span class="sxs-lookup"><span data-stu-id="d50ef-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="d50ef-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d50ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="d50ef-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d50ef-106">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="d50ef-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="d50ef-107">[in] `true` 執行驗證，即使需要覆寫登錄設定也一樣。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="d50ef-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="d50ef-108">在從 ECMA 公開金鑰到用於驗證之實際金鑰的對應指標。</span><span class="sxs-lookup"><span data-stu-id="d50ef-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="d50ef-109">在實際 ECMA 公用金鑰的長度。</span><span class="sxs-lookup"><span data-stu-id="d50ef-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="d50ef-110">[out] `true` 是否已驗證強式名稱簽章;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="d50ef-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="d50ef-111">如果因為登錄設定而驗證成功，此參數也會設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d50ef-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d50ef-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d50ef-112">Return Value</span></span>  
 <span data-ttu-id="d50ef-113">如果驗證成功，則 `S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="d50ef-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d50ef-114">需求</span><span class="sxs-lookup"><span data-stu-id="d50ef-114">Requirements</span></span>  
 <span data-ttu-id="d50ef-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d50ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d50ef-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="d50ef-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d50ef-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d50ef-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d50ef-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d50ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50ef-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d50ef-119">See also</span></span>

- [<span data-ttu-id="d50ef-120">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="d50ef-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="d50ef-121">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="d50ef-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="d50ef-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d50ef-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
