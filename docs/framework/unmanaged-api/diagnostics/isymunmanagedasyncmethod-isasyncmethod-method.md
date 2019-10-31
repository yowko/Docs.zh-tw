---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129216"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="c65d4-102">ISymUnmanagedAsyncMethod::IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="c65d4-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="c65d4-103">檢查方法是否有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="c65d4-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="c65d4-104">如果這個方法傳回 `FALSE` 則在此介面中呼叫任何其他方法是不正確。</span><span class="sxs-lookup"><span data-stu-id="c65d4-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="c65d4-105">在此情況下，它們全都會傳回 `E_UNEXPECTED`。</span><span class="sxs-lookup"><span data-stu-id="c65d4-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65d4-106">語法</span><span class="sxs-lookup"><span data-stu-id="c65d4-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c65d4-107">參數</span><span class="sxs-lookup"><span data-stu-id="c65d4-107">Parameters</span></span>  
  
|<span data-ttu-id="c65d4-108">參數</span><span class="sxs-lookup"><span data-stu-id="c65d4-108">Parameter</span></span>|<span data-ttu-id="c65d4-109">描述</span><span class="sxs-lookup"><span data-stu-id="c65d4-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="c65d4-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="c65d4-110">Return Value</span></span>  
 <span data-ttu-id="c65d4-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="c65d4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65d4-112">需求</span><span class="sxs-lookup"><span data-stu-id="c65d4-112">Requirements</span></span>  
 <span data-ttu-id="c65d4-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c65d4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65d4-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="c65d4-114">See also</span></span>

- [<span data-ttu-id="c65d4-115">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c65d4-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
