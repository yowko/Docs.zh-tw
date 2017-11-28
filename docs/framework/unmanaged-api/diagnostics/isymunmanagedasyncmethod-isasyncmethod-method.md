---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce91552d7468579d9941c1da75c4d281999d66fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="6c322-102">ISymUnmanagedAsyncMethod::IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="6c322-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="6c322-103">檢查是否方法或不具有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="6c322-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="6c322-104">如果此方法傳回`FALSE`則是無效的呼叫這個介面中的其他任何方法。</span><span class="sxs-lookup"><span data-stu-id="6c322-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="6c322-105">它們會傳回所有`E_UNEXPECTED`在此情況下。</span><span class="sxs-lookup"><span data-stu-id="6c322-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c322-106">語法</span><span class="sxs-lookup"><span data-stu-id="6c322-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c322-107">參數</span><span class="sxs-lookup"><span data-stu-id="6c322-107">Parameters</span></span>  
  
|<span data-ttu-id="6c322-108">參數</span><span class="sxs-lookup"><span data-stu-id="6c322-108">Parameter</span></span>|<span data-ttu-id="6c322-109">說明</span><span class="sxs-lookup"><span data-stu-id="6c322-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="6c322-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c322-110">Return Value</span></span>  
 <span data-ttu-id="6c322-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="6c322-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c322-112">需求</span><span class="sxs-lookup"><span data-stu-id="6c322-112">Requirements</span></span>  
 <span data-ttu-id="6c322-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c322-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c322-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c322-114">See Also</span></span>  
 [<span data-ttu-id="6c322-115">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="6c322-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
