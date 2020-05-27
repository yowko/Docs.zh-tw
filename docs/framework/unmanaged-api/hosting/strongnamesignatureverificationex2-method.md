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
ms.openlocfilehash: 5e6f77b9b5da061a75d23d7f3f7b673754b62afd
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006359"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="2568d-102">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="2568d-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="2568d-103">驗證強式名稱元件的簽章，並提供從 ECMA 金鑰到實際金鑰的對應。</span><span class="sxs-lookup"><span data-stu-id="2568d-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2568d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2568d-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2568d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2568d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2568d-106">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="2568d-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="2568d-107">[in] `true`若要執行驗證，即使需要覆寫登錄設定也一樣。否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="2568d-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="2568d-108">在從 ECMA 公開金鑰到用於驗證之實際金鑰的對應指標。</span><span class="sxs-lookup"><span data-stu-id="2568d-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="2568d-109">在實際 ECMA 公用金鑰的長度。</span><span class="sxs-lookup"><span data-stu-id="2568d-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="2568d-110">[out] `true`如果已驗證強式名稱簽章，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="2568d-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="2568d-111">如果因為登錄設定而驗證成功，此參數也會設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="2568d-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2568d-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2568d-112">Return Value</span></span>  
 <span data-ttu-id="2568d-113">`S_OK`如果驗證成功，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="2568d-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2568d-114">需求</span><span class="sxs-lookup"><span data-stu-id="2568d-114">Requirements</span></span>  
 <span data-ttu-id="2568d-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2568d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2568d-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="2568d-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2568d-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2568d-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2568d-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2568d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2568d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2568d-119">See also</span></span>

- [<span data-ttu-id="2568d-120">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="2568d-120">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="2568d-121">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="2568d-121">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="2568d-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="2568d-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
