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
ms.openlocfilehash: 0f4fdcbdfb9db7664920a42b9406a58f9c2de0b8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763107"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="17cbc-102">ICLRStrongName::StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="17cbc-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="17cbc-103">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="17cbc-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17cbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="17cbc-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17cbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="17cbc-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="17cbc-106">在用來計算緩衝區大小的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="17cbc-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="17cbc-107">脫銷傳回的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="17cbc-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17cbc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="17cbc-108">Return Value</span></span>  
 <span data-ttu-id="17cbc-109">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="17cbc-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cbc-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="17cbc-110">Requirements</span></span>  
 <span data-ttu-id="17cbc-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17cbc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cbc-112">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="17cbc-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="17cbc-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="17cbc-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17cbc-114">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cbc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cbc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17cbc-115">See also</span></span>

- [<span data-ttu-id="17cbc-116">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="17cbc-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
