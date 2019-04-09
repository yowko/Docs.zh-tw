---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196745"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="73030-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="73030-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="73030-103">設定的 IL 偏移編譯器所產生的 catch 處理常式包裝非同步方法。</span><span class="sxs-lookup"><span data-stu-id="73030-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="73030-104">產生的 catch 的 IL 位移偵錯工具用於處理 catch，如同它是非使用者程式碼，即使它可能會發生在使用者程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="73030-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="73030-105">特別是，它會在回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="73030-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73030-106">語法</span><span class="sxs-lookup"><span data-stu-id="73030-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73030-107">參數</span><span class="sxs-lookup"><span data-stu-id="73030-107">Parameters</span></span>  
  
|<span data-ttu-id="73030-108">參數</span><span class="sxs-lookup"><span data-stu-id="73030-108">Parameter</span></span>|<span data-ttu-id="73030-109">描述</span><span class="sxs-lookup"><span data-stu-id="73030-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="73030-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="73030-110">Return Value</span></span>  
 <span data-ttu-id="73030-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="73030-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73030-112">需求</span><span class="sxs-lookup"><span data-stu-id="73030-112">Requirements</span></span>  
 <span data-ttu-id="73030-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="73030-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73030-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73030-114">See also</span></span>

- [<span data-ttu-id="73030-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="73030-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
