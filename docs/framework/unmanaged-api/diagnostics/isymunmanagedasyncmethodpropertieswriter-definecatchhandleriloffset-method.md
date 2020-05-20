---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441769"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="97955-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="97955-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="97955-103">設定編譯器所產生的 catch 處理常式（包裝非同步方法）的 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="97955-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="97955-104">產生之 catch 的 IL 位移會由偵錯工具用來處理 catch，如同它是非使用者程式碼，即使它可能發生在使用者程式碼方法中也一樣。</span><span class="sxs-lookup"><span data-stu-id="97955-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="97955-105">特別是，它是用來回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="97955-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97955-106">語法</span><span class="sxs-lookup"><span data-stu-id="97955-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97955-107">參數</span><span class="sxs-lookup"><span data-stu-id="97955-107">Parameters</span></span>  
  
|<span data-ttu-id="97955-108">參數</span><span class="sxs-lookup"><span data-stu-id="97955-108">Parameter</span></span>|<span data-ttu-id="97955-109">說明</span><span class="sxs-lookup"><span data-stu-id="97955-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="97955-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="97955-110">Return Value</span></span>  
 <span data-ttu-id="97955-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="97955-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97955-112">需求</span><span class="sxs-lookup"><span data-stu-id="97955-112">Requirements</span></span>  
 <span data-ttu-id="97955-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="97955-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97955-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97955-114">See also</span></span>

- [<span data-ttu-id="97955-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="97955-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
