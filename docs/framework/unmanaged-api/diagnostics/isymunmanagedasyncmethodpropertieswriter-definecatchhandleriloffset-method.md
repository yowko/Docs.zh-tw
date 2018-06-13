---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425427"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="f3db2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f3db2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="f3db2-103">設定的 IL 位移編譯器產生的 catch 處理常式所包裝的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="f3db2-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="f3db2-104">產生 catch 的 IL 位移偵錯工具用於 catch 處理視為非使用者程式碼即使它可能會發生在使用者程式碼方法。</span><span class="sxs-lookup"><span data-stu-id="f3db2-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="f3db2-105">特別是，它用於回應**CatchHandlerFound**例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="f3db2-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3db2-106">語法</span><span class="sxs-lookup"><span data-stu-id="f3db2-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3db2-107">參數</span><span class="sxs-lookup"><span data-stu-id="f3db2-107">Parameters</span></span>  
  
|<span data-ttu-id="f3db2-108">參數</span><span class="sxs-lookup"><span data-stu-id="f3db2-108">Parameter</span></span>|<span data-ttu-id="f3db2-109">描述</span><span class="sxs-lookup"><span data-stu-id="f3db2-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="f3db2-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3db2-110">Return Value</span></span>  
 <span data-ttu-id="f3db2-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="f3db2-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3db2-112">需求</span><span class="sxs-lookup"><span data-stu-id="f3db2-112">Requirements</span></span>  
 <span data-ttu-id="f3db2-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3db2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3db2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3db2-114">See Also</span></span>  
 [<span data-ttu-id="f3db2-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="f3db2-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
