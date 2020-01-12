---
title: ICLRStrongName::GetHashFromBlob 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: b42079d138e754996470e07b884d49c1ebb625c3
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901160"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="036cd-102">ICLRStrongName::GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="036cd-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="036cd-103">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="036cd-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="036cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="036cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="036cd-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="036cd-106">在要雜湊的記憶體區塊位址的指標。</span><span class="sxs-lookup"><span data-stu-id="036cd-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="036cd-107">在記憶體區塊的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="036cd-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="036cd-108">[in、out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="036cd-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="036cd-109">預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="036cd-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="036cd-110">脫銷傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="036cd-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="036cd-111">在`pbHash`的要求大小上限。</span><span class="sxs-lookup"><span data-stu-id="036cd-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="036cd-112">脫銷傳回之 `pbHash`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="036cd-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="036cd-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="036cd-113">Return Value</span></span>  
 <span data-ttu-id="036cd-114">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="036cd-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036cd-115">需求</span><span class="sxs-lookup"><span data-stu-id="036cd-115">Requirements</span></span>  
 <span data-ttu-id="036cd-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="036cd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036cd-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="036cd-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="036cd-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="036cd-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="036cd-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036cd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036cd-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="036cd-120">See also</span></span>

- [<span data-ttu-id="036cd-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="036cd-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
