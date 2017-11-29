---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3bae0e2dfb56883a674b282acd385ba45a25bebb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="bbe05-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="bbe05-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="bbe05-103">設定的 IL 位移編譯器產生的 catch 處理常式所包裝的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="bbe05-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="bbe05-104">產生 catch 的 IL 位移偵錯工具用於 catch 處理視為非使用者程式碼即使它可能會發生在使用者程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="bbe05-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="bbe05-105">特別是，它用於回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="bbe05-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe05-106">語法</span><span class="sxs-lookup"><span data-stu-id="bbe05-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbe05-107">參數</span><span class="sxs-lookup"><span data-stu-id="bbe05-107">Parameters</span></span>  
  
|<span data-ttu-id="bbe05-108">參數</span><span class="sxs-lookup"><span data-stu-id="bbe05-108">Parameter</span></span>|<span data-ttu-id="bbe05-109">說明</span><span class="sxs-lookup"><span data-stu-id="bbe05-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="bbe05-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="bbe05-110">Return Value</span></span>  
 <span data-ttu-id="bbe05-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="bbe05-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe05-112">需求</span><span class="sxs-lookup"><span data-stu-id="bbe05-112">Requirements</span></span>  
 <span data-ttu-id="bbe05-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bbe05-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe05-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbe05-114">See Also</span></span>  
 [<span data-ttu-id="bbe05-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bbe05-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
