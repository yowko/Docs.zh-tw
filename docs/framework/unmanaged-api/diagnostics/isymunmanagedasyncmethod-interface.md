---
title: ISymUnmanagedAsyncMethod 介面
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 0b8adba9dbffbdc47bb526cef9aad3ffa4b48065
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129218"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="a52f0-102">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="a52f0-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="a52f0-103">這個介面是[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。</span><span class="sxs-lookup"><span data-stu-id="a52f0-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a52f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a52f0-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="a52f0-105">方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-105">Methods</span></span>  
 <span data-ttu-id="a52f0-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="a52f0-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="a52f0-107">方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-107">Method</span></span>|<span data-ttu-id="a52f0-108">描述</span><span class="sxs-lookup"><span data-stu-id="a52f0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a52f0-109">GetAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="a52f0-110">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a52f0-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="a52f0-111">GetAsyncStepInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="a52f0-112">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a52f0-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="a52f0-113">GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="a52f0-114">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a52f0-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="a52f0-115">GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="a52f0-116">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a52f0-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="a52f0-117">HasCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="a52f0-118">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a52f0-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="a52f0-119">IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="a52f0-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="a52f0-120">檢查方法是否有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="a52f0-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="a52f0-121">如果這個方法傳回 `FALSE` 則在此介面中呼叫任何其他方法是不正確。</span><span class="sxs-lookup"><span data-stu-id="a52f0-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="a52f0-122">在此情況下，它們全都會傳回 `E_UNEXPECTED`。</span><span class="sxs-lookup"><span data-stu-id="a52f0-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a52f0-123">需求</span><span class="sxs-lookup"><span data-stu-id="a52f0-123">Requirements</span></span>  
 <span data-ttu-id="a52f0-124">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a52f0-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a52f0-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="a52f0-125">See also</span></span>

- [<span data-ttu-id="a52f0-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="a52f0-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
