---
title: ISymUnmanagedAsyncMethodPropertiesWriter 介面
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82fcddd7a3f89a92cc79285930b30342333fbec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940097"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="61391-102">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="61391-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="61391-103">可讓您定義每個方法符號的選擇性的非同步方法資訊。</span><span class="sxs-lookup"><span data-stu-id="61391-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="61391-104">一律使用具有已開啟的方法。也就是呼叫之間[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)並[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="61391-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61391-105">語法</span><span class="sxs-lookup"><span data-stu-id="61391-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="61391-106">方法</span><span class="sxs-lookup"><span data-stu-id="61391-106">Methods</span></span>  
 <span data-ttu-id="61391-107">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="61391-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="61391-108">方法</span><span class="sxs-lookup"><span data-stu-id="61391-108">Method</span></span>|<span data-ttu-id="61391-109">描述</span><span class="sxs-lookup"><span data-stu-id="61391-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61391-110">DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="61391-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="61391-111">定義一組非同步等候目前的方法中的作業。</span><span class="sxs-lookup"><span data-stu-id="61391-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="61391-112">每個 yield 位移符合 await 傳回指示，用來識別潛在的暫止。</span><span class="sxs-lookup"><span data-stu-id="61391-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="61391-113">每個`breakpointMethod` / `breakpointOffset`組可讓您識別會在繼續執行非同步作業; 它可能位於不同的方法。</span><span class="sxs-lookup"><span data-stu-id="61391-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="61391-114">DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="61391-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="61391-115">設定的 IL 偏移編譯器所產生的 catch 處理常式包裝非同步方法。</span><span class="sxs-lookup"><span data-stu-id="61391-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="61391-116">產生的 catch 的 IL 位移偵錯工具用於 catch 處理視為非使用者程式碼，即使它可能會發生在使用者程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="61391-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="61391-117">特別是，它會在回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="61391-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="61391-118">DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="61391-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="61391-119">設定啟始非同步作業的開始方法。</span><span class="sxs-lookup"><span data-stu-id="61391-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61391-120">需求</span><span class="sxs-lookup"><span data-stu-id="61391-120">Requirements</span></span>  
 <span data-ttu-id="61391-121">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61391-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61391-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61391-122">See also</span></span>

- [<span data-ttu-id="61391-123">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="61391-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
