---
title: ISymUnmanagedAsyncMethodPropertiesWriter 介面
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129156"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="bf2f9-102">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bf2f9-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="bf2f9-103">可讓您定義每個方法符號的選擇性非同步方法資訊。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="bf2f9-104">一律搭配已開啟的方法使用;也就是呼叫[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)之間的。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf2f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="bf2f9-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="bf2f9-106">方法</span><span class="sxs-lookup"><span data-stu-id="bf2f9-106">Methods</span></span>  
 <span data-ttu-id="bf2f9-107">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="bf2f9-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="bf2f9-108">方法</span><span class="sxs-lookup"><span data-stu-id="bf2f9-108">Method</span></span>|<span data-ttu-id="bf2f9-109">描述</span><span class="sxs-lookup"><span data-stu-id="bf2f9-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf2f9-110">DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="bf2f9-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="bf2f9-111">在目前方法中定義非同步 await 作業的群組。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="bf2f9-112">每個產生位移都會符合 await 的傳回指示，以識別潛在的收益。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="bf2f9-113">每個 `breakpointMethod`/`breakpointOffset` 組都會識別非同步作業的繼續位置;它可能是在不同的方法中。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="bf2f9-114">DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="bf2f9-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="bf2f9-115">設定編譯器所產生的 catch 處理常式（包裝非同步方法）的 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="bf2f9-116">產生之 catch 的 IL 位移會由偵錯工具用來處理 catch，就好像它是非使用者程式碼一樣，即使它可能發生在使用者程式碼方法中也一樣。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="bf2f9-117">特別是，它是用來回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="bf2f9-118">DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="bf2f9-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="bf2f9-119">設定啟動非同步作業的起始方法。</span><span class="sxs-lookup"><span data-stu-id="bf2f9-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf2f9-120">需求</span><span class="sxs-lookup"><span data-stu-id="bf2f9-120">Requirements</span></span>  
 <span data-ttu-id="bf2f9-121">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bf2f9-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2f9-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf2f9-122">See also</span></span>

- [<span data-ttu-id="bf2f9-123">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="bf2f9-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
