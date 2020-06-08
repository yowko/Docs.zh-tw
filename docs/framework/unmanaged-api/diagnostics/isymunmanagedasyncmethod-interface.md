---
title: ISymUnmanagedAsyncMethod 介面
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504448"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="18ce2-102">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="18ce2-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="18ce2-103">這個介面是[ISymUnmanagedAsyncMethodPropertiesWriter 介面](isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。</span><span class="sxs-lookup"><span data-stu-id="18ce2-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ce2-104">語法</span><span class="sxs-lookup"><span data-stu-id="18ce2-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="18ce2-105">方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-105">Methods</span></span>  
 <span data-ttu-id="18ce2-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="18ce2-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="18ce2-107">方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-107">Method</span></span>|<span data-ttu-id="18ce2-108">描述</span><span class="sxs-lookup"><span data-stu-id="18ce2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18ce2-109">GetAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="18ce2-110">請參閱[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="18ce2-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="18ce2-111">GetAsyncStepInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="18ce2-112">請參閱[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="18ce2-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="18ce2-113">GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="18ce2-114">請參閱[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="18ce2-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="18ce2-115">GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="18ce2-116">請參閱[DefineKickoffMethod 方法](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="18ce2-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="18ce2-117">HasCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="18ce2-118">請參閱[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="18ce2-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="18ce2-119">IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="18ce2-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="18ce2-120">檢查方法是否有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="18ce2-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="18ce2-121">如果這個方法傳回，則 `FALSE` 呼叫這個介面中的任何其他方法是不正確。</span><span class="sxs-lookup"><span data-stu-id="18ce2-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="18ce2-122">`E_UNEXPECTED`在此情況下，它們全部都會傳回。</span><span class="sxs-lookup"><span data-stu-id="18ce2-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18ce2-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="18ce2-123">Requirements</span></span>  
 <span data-ttu-id="18ce2-124">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="18ce2-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ce2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18ce2-125">See also</span></span>

- [<span data-ttu-id="18ce2-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="18ce2-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
