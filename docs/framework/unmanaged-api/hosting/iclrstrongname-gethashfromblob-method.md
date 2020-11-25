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
ms.openlocfilehash: 6b67aed90585f57d2635bb1a22d3e009edf01159
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714805"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="3f17e-102">ICLRStrongName::GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="3f17e-102">ICLRStrongName::GetHashFromBlob Method</span></span>

<span data-ttu-id="3f17e-103">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="3f17e-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f17e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f17e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3f17e-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f17e-105">Parameters</span></span>  

 `pbBlob`  
 <span data-ttu-id="3f17e-106">在要雜湊之記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="3f17e-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="3f17e-107">在記憶體區塊的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3f17e-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3f17e-108">[in，out]指定雜湊演算法的常數。</span><span class="sxs-lookup"><span data-stu-id="3f17e-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="3f17e-109">針對預設演算法使用零。</span><span class="sxs-lookup"><span data-stu-id="3f17e-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3f17e-110">擴展傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3f17e-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3f17e-111">在要求的大小上限 `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="3f17e-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3f17e-112">擴展傳回之的大小（以位元組為單位） `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="3f17e-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f17e-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f17e-113">Return Value</span></span>  

 <span data-ttu-id="3f17e-114">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="3f17e-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f17e-115">需求</span><span class="sxs-lookup"><span data-stu-id="3f17e-115">Requirements</span></span>  

 <span data-ttu-id="3f17e-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f17e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f17e-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="3f17e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3f17e-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3f17e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f17e-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f17e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f17e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f17e-120">See also</span></span>

- [<span data-ttu-id="3f17e-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="3f17e-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
