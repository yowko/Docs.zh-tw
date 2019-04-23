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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0708a3b501a99b5f71be5ba4c6cc4ea2b754d12a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191337"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="bcde4-102">IDebuggerInfo::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="bcde4-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="bcde4-103">取得值，指出是否要將受管理的偵錯工具附加至這個處理程序。</span><span class="sxs-lookup"><span data-stu-id="bcde4-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcde4-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcde4-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcde4-105">參數</span><span class="sxs-lookup"><span data-stu-id="bcde4-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="bcde4-106">[out]為值的指標`true`managed 偵錯工具附加至處理序，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="bcde4-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcde4-107">需求</span><span class="sxs-lookup"><span data-stu-id="bcde4-107">Requirements</span></span>  
 <span data-ttu-id="bcde4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcde4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcde4-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bcde4-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcde4-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bcde4-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcde4-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcde4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcde4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcde4-112">See also</span></span>

- [<span data-ttu-id="bcde4-113">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bcde4-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
