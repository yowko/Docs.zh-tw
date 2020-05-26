---
title: IDebuggerInfo::IsDebuggerAttached 方法
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: 95b7a2f6d35104c3353853549dacc783355feb5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805340"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="6263e-102">IDebuggerInfo::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="6263e-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="6263e-103">取得值，指出 managed 偵錯工具是否附加至此進程。</span><span class="sxs-lookup"><span data-stu-id="6263e-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6263e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6263e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6263e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6263e-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="6263e-106">脫銷值的指標， `true` 如果 managed 偵錯工具附加至進程，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6263e-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6263e-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="6263e-107">Requirements</span></span>  
 <span data-ttu-id="6263e-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6263e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6263e-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6263e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6263e-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6263e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6263e-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6263e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6263e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6263e-112">See also</span></span>

- [<span data-ttu-id="6263e-113">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6263e-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)
