---
title: ICLRStrongName::StrongNameHashSize 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: abcae4a89dc2ee3895d6ff246fa7358a5fe2f06e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901119"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="7bf9c-102">ICLRStrongName::StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="7bf9c-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="7bf9c-103">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="7bf9c-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bf9c-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bf9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bf9c-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="7bf9c-106">在用來計算緩衝區大小的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="7bf9c-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="7bf9c-107">脫銷傳回的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7bf9c-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bf9c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bf9c-108">Return Value</span></span>  
 <span data-ttu-id="7bf9c-109">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="7bf9c-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf9c-110">需求</span><span class="sxs-lookup"><span data-stu-id="7bf9c-110">Requirements</span></span>  
 <span data-ttu-id="7bf9c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bf9c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf9c-112">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="7bf9c-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7bf9c-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7bf9c-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bf9c-114">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf9c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf9c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="7bf9c-115">See also</span></span>

- [<span data-ttu-id="7bf9c-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="7bf9c-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
