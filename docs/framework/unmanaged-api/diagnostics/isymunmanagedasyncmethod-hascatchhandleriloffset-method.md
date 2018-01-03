---
title: "ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9ce105c-6495-49ab-b0e5-903a48ebadb3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5aaad64a5e5888852dc41e7397ca5014d50ea56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodhascatchhandleriloffset-method"></a><span data-ttu-id="9d227-102">ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9d227-102">ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset Method</span></span>
<span data-ttu-id="9d227-103">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9d227-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d227-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d227-104">Syntax</span></span>  
  
```idl  
HRESULT HasCatchHandlerILOffset(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d227-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d227-105">Parameters</span></span>  
  
|<span data-ttu-id="9d227-106">參數</span><span class="sxs-lookup"><span data-stu-id="9d227-106">Parameter</span></span>|<span data-ttu-id="9d227-107">描述</span><span class="sxs-lookup"><span data-stu-id="9d227-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="9d227-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d227-108">Return Value</span></span>  
 <span data-ttu-id="9d227-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="9d227-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d227-110">需求</span><span class="sxs-lookup"><span data-stu-id="9d227-110">Requirements</span></span>  
 <span data-ttu-id="9d227-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9d227-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d227-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="9d227-112">See Also</span></span>  
 [<span data-ttu-id="9d227-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="9d227-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
