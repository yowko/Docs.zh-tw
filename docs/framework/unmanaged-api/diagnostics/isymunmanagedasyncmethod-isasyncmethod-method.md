---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f5bf8252986ffa90ea5380d5342595cb91e5419
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424937"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="13c7e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="13c7e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="13c7e-103">檢查是否方法或不具有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="13c7e-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="13c7e-104">如果此方法傳回`FALSE`則是無效的呼叫這個介面中的其他任何方法。</span><span class="sxs-lookup"><span data-stu-id="13c7e-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="13c7e-105">它們會傳回所有`E_UNEXPECTED`在此情況下。</span><span class="sxs-lookup"><span data-stu-id="13c7e-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c7e-106">語法</span><span class="sxs-lookup"><span data-stu-id="13c7e-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13c7e-107">參數</span><span class="sxs-lookup"><span data-stu-id="13c7e-107">Parameters</span></span>  
  
|<span data-ttu-id="13c7e-108">參數</span><span class="sxs-lookup"><span data-stu-id="13c7e-108">Parameter</span></span>|<span data-ttu-id="13c7e-109">描述</span><span class="sxs-lookup"><span data-stu-id="13c7e-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="13c7e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="13c7e-110">Return Value</span></span>  
 <span data-ttu-id="13c7e-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="13c7e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c7e-112">需求</span><span class="sxs-lookup"><span data-stu-id="13c7e-112">Requirements</span></span>  
 <span data-ttu-id="13c7e-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="13c7e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c7e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13c7e-114">See Also</span></span>  
 [<span data-ttu-id="13c7e-115">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="13c7e-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
