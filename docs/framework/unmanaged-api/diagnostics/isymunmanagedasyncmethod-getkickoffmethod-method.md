---
title: "ISymUnmanagedAsyncMethod::GetKickoffMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 866632b3916cd2e35e7832c4d58b5988fa350c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="7e2a8-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="7e2a8-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="7e2a8-103">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="7e2a8-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e2a8-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e2a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e2a8-105">Parameters</span></span>  
  
|<span data-ttu-id="7e2a8-106">參數</span><span class="sxs-lookup"><span data-stu-id="7e2a8-106">Parameter</span></span>|<span data-ttu-id="7e2a8-107">描述</span><span class="sxs-lookup"><span data-stu-id="7e2a8-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7e2a8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7e2a8-108">Return Value</span></span>  
 <span data-ttu-id="7e2a8-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="7e2a8-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e2a8-110">需求</span><span class="sxs-lookup"><span data-stu-id="7e2a8-110">Requirements</span></span>  
 <span data-ttu-id="7e2a8-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7e2a8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2a8-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e2a8-112">See Also</span></span>  
 [<span data-ttu-id="7e2a8-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="7e2a8-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
