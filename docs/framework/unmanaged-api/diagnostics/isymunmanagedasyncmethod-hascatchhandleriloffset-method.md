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
ms.openlocfilehash: 561a4d62860feb4e56aa3a3552544c4dfb7a001e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodhascatchhandleriloffset-method"></a><span data-ttu-id="8234f-102">ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8234f-102">ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset Method</span></span>
<span data-ttu-id="8234f-103">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8234f-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8234f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8234f-104">Syntax</span></span>  
  
```idl  
HRESULT HasCatchHandlerILOffset(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8234f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8234f-105">Parameters</span></span>  
  
|<span data-ttu-id="8234f-106">參數</span><span class="sxs-lookup"><span data-stu-id="8234f-106">Parameter</span></span>|<span data-ttu-id="8234f-107">說明</span><span class="sxs-lookup"><span data-stu-id="8234f-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="8234f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8234f-108">Return Value</span></span>  
 <span data-ttu-id="8234f-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="8234f-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8234f-110">需求</span><span class="sxs-lookup"><span data-stu-id="8234f-110">Requirements</span></span>  
 <span data-ttu-id="8234f-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8234f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8234f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8234f-112">See Also</span></span>  
 [<span data-ttu-id="8234f-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="8234f-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
