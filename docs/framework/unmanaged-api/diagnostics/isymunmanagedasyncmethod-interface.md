---
title: ISymUnmanagedAsyncMethod 介面
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cefad27d8b9314b45dec6100e35a54990fb591c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427995"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="0951b-102">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="0951b-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="0951b-103">這個介面是讀取補數[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="0951b-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0951b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0951b-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="0951b-105">方法</span><span class="sxs-lookup"><span data-stu-id="0951b-105">Methods</span></span>  
 <span data-ttu-id="0951b-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="0951b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0951b-107">方法</span><span class="sxs-lookup"><span data-stu-id="0951b-107">Method</span></span>|<span data-ttu-id="0951b-108">描述</span><span class="sxs-lookup"><span data-stu-id="0951b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0951b-109">GetAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="0951b-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="0951b-110">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0951b-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="0951b-111">GetAsyncStepInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="0951b-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="0951b-112">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0951b-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="0951b-113">GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="0951b-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="0951b-114">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0951b-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="0951b-115">GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="0951b-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="0951b-116">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0951b-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="0951b-117">HasCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="0951b-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="0951b-118">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0951b-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="0951b-119">IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="0951b-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="0951b-120">檢查是否方法或不具有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="0951b-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="0951b-121">如果此方法傳回`FALSE`則是無效的呼叫這個介面中的其他任何方法。</span><span class="sxs-lookup"><span data-stu-id="0951b-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="0951b-122">它們會傳回所有`E_UNEXPECTED`在此情況下。</span><span class="sxs-lookup"><span data-stu-id="0951b-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0951b-123">需求</span><span class="sxs-lookup"><span data-stu-id="0951b-123">Requirements</span></span>  
 <span data-ttu-id="0951b-124">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0951b-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0951b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0951b-125">See Also</span></span>  
 [<span data-ttu-id="0951b-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="0951b-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
