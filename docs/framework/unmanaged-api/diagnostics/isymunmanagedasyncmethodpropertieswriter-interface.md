---
title: ISymUnmanagedAsyncMethodPropertiesWriter 介面
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 779b737da43f61d1023a0a640dce936e11c4704c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707031"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="e70bf-102">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="e70bf-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>

<span data-ttu-id="e70bf-103">可讓您為每個方法符號定義選擇性的非同步方法資訊。</span><span class="sxs-lookup"><span data-stu-id="e70bf-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="e70bf-104">一律與開啟的方法搭配使用;也就是說，呼叫 [OpenMethod 方法](isymunmanagedwriter-openmethod-method.md) 和 [CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)之間的。</span><span class="sxs-lookup"><span data-stu-id="e70bf-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70bf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e70bf-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="e70bf-106">方法</span><span class="sxs-lookup"><span data-stu-id="e70bf-106">Methods</span></span>  

 <span data-ttu-id="e70bf-107">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="e70bf-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e70bf-108">方法</span><span class="sxs-lookup"><span data-stu-id="e70bf-108">Method</span></span>|<span data-ttu-id="e70bf-109">描述</span><span class="sxs-lookup"><span data-stu-id="e70bf-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e70bf-110">DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="e70bf-110">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="e70bf-111">在目前方法中定義非同步 await 作業的群組。</span><span class="sxs-lookup"><span data-stu-id="e70bf-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="e70bf-112">每個 yield 位移都符合 await 的傳回指令，以識別潛在的 yield。</span><span class="sxs-lookup"><span data-stu-id="e70bf-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="e70bf-113">每一組 `breakpointMethod` / `breakpointOffset` 都會識別非同步作業將繼續的位置; 它可能在不同的方法中。</span><span class="sxs-lookup"><span data-stu-id="e70bf-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="e70bf-114">DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="e70bf-114">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="e70bf-115">針對包裝非同步方法的編譯器產生的 catch 處理常式，設定 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="e70bf-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="e70bf-116">偵錯工具會使用所產生之 catch 的 IL 位移來處理 catch，如同非使用者程式碼，即使它可能發生在使用者程式碼方法中也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e70bf-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="e70bf-117">尤其是，它是用來回應 **CatchHandlerFound** 例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="e70bf-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="e70bf-118">DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="e70bf-118">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="e70bf-119">設定啟動非同步作業的起始方法。</span><span class="sxs-lookup"><span data-stu-id="e70bf-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e70bf-120">需求</span><span class="sxs-lookup"><span data-stu-id="e70bf-120">Requirements</span></span>  

 <span data-ttu-id="e70bf-121">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e70bf-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70bf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e70bf-122">See also</span></span>

- [<span data-ttu-id="e70bf-123">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="e70bf-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
