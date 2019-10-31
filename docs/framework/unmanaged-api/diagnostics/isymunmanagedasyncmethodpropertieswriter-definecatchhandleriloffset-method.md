---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: b108c8c87d3afdbfacb569ab501274e5c45c2e2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129180"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="3e70f-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="3e70f-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="3e70f-103">設定編譯器所產生的 catch 處理常式（包裝非同步方法）的 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="3e70f-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="3e70f-104">產生之 catch 的 IL 位移會由偵錯工具用來處理 catch，如同它是非使用者程式碼，即使它可能發生在使用者程式碼方法中也一樣。</span><span class="sxs-lookup"><span data-stu-id="3e70f-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="3e70f-105">特別是，它是用來回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="3e70f-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e70f-106">語法</span><span class="sxs-lookup"><span data-stu-id="3e70f-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e70f-107">參數</span><span class="sxs-lookup"><span data-stu-id="3e70f-107">Parameters</span></span>  
  
|<span data-ttu-id="3e70f-108">參數</span><span class="sxs-lookup"><span data-stu-id="3e70f-108">Parameter</span></span>|<span data-ttu-id="3e70f-109">描述</span><span class="sxs-lookup"><span data-stu-id="3e70f-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="3e70f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="3e70f-110">Return Value</span></span>  
 <span data-ttu-id="3e70f-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="3e70f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e70f-112">需求</span><span class="sxs-lookup"><span data-stu-id="3e70f-112">Requirements</span></span>  
 <span data-ttu-id="3e70f-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3e70f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e70f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e70f-114">See also</span></span>

- [<span data-ttu-id="3e70f-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="3e70f-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
