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
ms.openlocfilehash: 81640e8e34335898f4dd7f4f43eafbd3ef191d19
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938161"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="04492-102">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="04492-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="04492-103">驗證強式名稱元件的簽章，並提供從 ECMA 金鑰到實際金鑰的對應。</span><span class="sxs-lookup"><span data-stu-id="04492-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04492-104">語法</span><span class="sxs-lookup"><span data-stu-id="04492-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04492-105">參數</span><span class="sxs-lookup"><span data-stu-id="04492-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="04492-106">在要驗證之元件的可攜式可執行檔（.exe 或 .dll）的路徑。</span><span class="sxs-lookup"><span data-stu-id="04492-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="04492-107">[in] `true` 執行驗證，即使需要覆寫登錄設定也一樣。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="04492-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="04492-108">在從 ECMA 公開金鑰到用於驗證之實際金鑰的對應指標。</span><span class="sxs-lookup"><span data-stu-id="04492-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="04492-109">在實際 ECMA 公用金鑰的長度。</span><span class="sxs-lookup"><span data-stu-id="04492-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="04492-110">[out] `true` 是否已驗證強式名稱簽章;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="04492-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="04492-111">如果因為登錄設定而驗證成功，此參數也會設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="04492-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04492-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="04492-112">Return Value</span></span>  
 <span data-ttu-id="04492-113">如果驗證成功，則 `S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="04492-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04492-114">需求</span><span class="sxs-lookup"><span data-stu-id="04492-114">Requirements</span></span>  
 <span data-ttu-id="04492-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04492-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04492-116">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="04492-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="04492-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="04492-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04492-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04492-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04492-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="04492-119">See also</span></span>

- [<span data-ttu-id="04492-120">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="04492-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="04492-121">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="04492-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="04492-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="04492-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
