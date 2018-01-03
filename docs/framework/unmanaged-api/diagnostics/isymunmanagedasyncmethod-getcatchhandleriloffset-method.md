---
title: "ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96040ee5f56ade3647367c4b879c8aa9e7f460fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="2f672-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="2f672-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="2f672-103">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2f672-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f672-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f672-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f672-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f672-105">Parameters</span></span>  
  
|<span data-ttu-id="2f672-106">參數</span><span class="sxs-lookup"><span data-stu-id="2f672-106">Parameter</span></span>|<span data-ttu-id="2f672-107">描述</span><span class="sxs-lookup"><span data-stu-id="2f672-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="2f672-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2f672-108">Return Value</span></span>  
 <span data-ttu-id="2f672-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="2f672-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f672-110">需求</span><span class="sxs-lookup"><span data-stu-id="2f672-110">Requirements</span></span>  
 <span data-ttu-id="2f672-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2f672-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f672-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f672-112">See Also</span></span>  
 [<span data-ttu-id="2f672-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="2f672-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
