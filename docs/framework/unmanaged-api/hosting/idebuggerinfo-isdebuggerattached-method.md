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
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133169"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="867de-102">IDebuggerInfo::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="867de-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="867de-103">取得值，指出 managed 偵錯工具是否附加至此進程。</span><span class="sxs-lookup"><span data-stu-id="867de-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="867de-104">語法</span><span class="sxs-lookup"><span data-stu-id="867de-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="867de-105">參數</span><span class="sxs-lookup"><span data-stu-id="867de-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="867de-106">脫銷如果 managed 偵錯工具附加至進程，則為 `true` 值的指標;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="867de-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="867de-107">需求</span><span class="sxs-lookup"><span data-stu-id="867de-107">Requirements</span></span>  
 <span data-ttu-id="867de-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="867de-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="867de-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="867de-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="867de-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="867de-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="867de-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="867de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867de-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="867de-112">See also</span></span>

- [<span data-ttu-id="867de-113">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="867de-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
