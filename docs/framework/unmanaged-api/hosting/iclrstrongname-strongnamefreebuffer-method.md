---
title: ICLRStrongName::StrongNameFreeBuffer 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 0f96ac606bd68226cbd657c3fc1aa7cf0ffc166b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726128"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="5c8f0-102">ICLRStrongName::StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="5c8f0-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>

<span data-ttu-id="5c8f0-103">釋放先前呼叫強式名稱方法（例如 [ICLRStrongName：： StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)、 [ICLRStrongName：： StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)或 [ICLRStrongName：： StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)）所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c8f0-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c8f0-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c8f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c8f0-105">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="5c8f0-106">在要釋放之記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="5c8f0-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c8f0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5c8f0-107">Return Value</span></span>  

 <span data-ttu-id="5c8f0-108">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="5c8f0-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c8f0-109">需求</span><span class="sxs-lookup"><span data-stu-id="5c8f0-109">Requirements</span></span>  

 <span data-ttu-id="5c8f0-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c8f0-111">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="5c8f0-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c8f0-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5c8f0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c8f0-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c8f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8f0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c8f0-114">See also</span></span>

- [<span data-ttu-id="5c8f0-115">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5c8f0-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
