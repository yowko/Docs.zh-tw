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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f84d50579feade09df1b42a8e2f0c6b3e6a94fac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157714"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="f6cba-102">ICLRStrongName::GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="f6cba-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="f6cba-103">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="f6cba-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6cba-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6cba-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6cba-105">參數</span><span class="sxs-lookup"><span data-stu-id="f6cba-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="f6cba-106">[in]要雜湊的記憶體區塊的位址指標。</span><span class="sxs-lookup"><span data-stu-id="f6cba-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="f6cba-107">[in]記憶體區塊的長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="f6cba-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f6cba-108">[in、 out]常數，指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="f6cba-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f6cba-109">使用零的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="f6cba-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f6cba-110">[out]傳回的雜湊緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f6cba-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f6cba-111">[in]要求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="f6cba-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f6cba-112">[out]大小，以位元組為單位傳回`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="f6cba-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6cba-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="f6cba-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="f6cba-114">如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="f6cba-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6cba-115">需求</span><span class="sxs-lookup"><span data-stu-id="f6cba-115">Requirements</span></span>  
 <span data-ttu-id="f6cba-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6cba-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6cba-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f6cba-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f6cba-118">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f6cba-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f6cba-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f6cba-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6cba-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6cba-120">See also</span></span>

- [<span data-ttu-id="f6cba-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f6cba-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
