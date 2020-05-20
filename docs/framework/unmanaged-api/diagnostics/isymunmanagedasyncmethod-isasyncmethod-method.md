---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441795"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="b62f3-102">ISymUnmanagedAsyncMethod::IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="b62f3-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="b62f3-103">檢查方法是否有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="b62f3-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="b62f3-104">如果這個方法傳回，則 `FALSE` 呼叫這個介面中的任何其他方法是不正確。</span><span class="sxs-lookup"><span data-stu-id="b62f3-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="b62f3-105">`E_UNEXPECTED`在此情況下，它們全部都會傳回。</span><span class="sxs-lookup"><span data-stu-id="b62f3-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b62f3-106">語法</span><span class="sxs-lookup"><span data-stu-id="b62f3-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b62f3-107">參數</span><span class="sxs-lookup"><span data-stu-id="b62f3-107">Parameters</span></span>  
  
|<span data-ttu-id="b62f3-108">參數</span><span class="sxs-lookup"><span data-stu-id="b62f3-108">Parameter</span></span>|<span data-ttu-id="b62f3-109">說明</span><span class="sxs-lookup"><span data-stu-id="b62f3-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="b62f3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b62f3-110">Return Value</span></span>  
 <span data-ttu-id="b62f3-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="b62f3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b62f3-112">需求</span><span class="sxs-lookup"><span data-stu-id="b62f3-112">Requirements</span></span>  
 <span data-ttu-id="b62f3-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="b62f3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62f3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b62f3-114">See also</span></span>

- [<span data-ttu-id="b62f3-115">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="b62f3-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
