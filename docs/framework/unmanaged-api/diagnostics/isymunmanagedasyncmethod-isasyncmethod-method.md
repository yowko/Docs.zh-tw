---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5cddf34f1a6277e966901c9692bff63e26a3b8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136730"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="e4932-102">ISymUnmanagedAsyncMethod::IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="e4932-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="e4932-103">檢查方法是否非同步處理的資訊。</span><span class="sxs-lookup"><span data-stu-id="e4932-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="e4932-104">如果此方法傳回`FALSE`則是在此介面中呼叫任何其他方法無效。</span><span class="sxs-lookup"><span data-stu-id="e4932-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="e4932-105">將所有傳回`E_UNEXPECTED`在此情況下。</span><span class="sxs-lookup"><span data-stu-id="e4932-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4932-106">語法</span><span class="sxs-lookup"><span data-stu-id="e4932-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4932-107">參數</span><span class="sxs-lookup"><span data-stu-id="e4932-107">Parameters</span></span>  
  
|<span data-ttu-id="e4932-108">參數</span><span class="sxs-lookup"><span data-stu-id="e4932-108">Parameter</span></span>|<span data-ttu-id="e4932-109">描述</span><span class="sxs-lookup"><span data-stu-id="e4932-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="e4932-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e4932-110">Return Value</span></span>  
 <span data-ttu-id="e4932-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="e4932-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4932-112">需求</span><span class="sxs-lookup"><span data-stu-id="e4932-112">Requirements</span></span>  
 <span data-ttu-id="e4932-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4932-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4932-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4932-114">See also</span></span>

- [<span data-ttu-id="e4932-115">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="e4932-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
