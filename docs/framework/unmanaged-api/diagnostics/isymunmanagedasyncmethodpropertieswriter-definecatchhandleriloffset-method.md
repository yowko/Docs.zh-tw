---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: a37d319a39b959700944f9e111d2945e286c99ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707135"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="9bef4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9bef4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>

<span data-ttu-id="9bef4-103">針對包裝非同步方法的編譯器產生的 catch 處理常式，設定 IL 位移。</span><span class="sxs-lookup"><span data-stu-id="9bef4-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="9bef4-104">偵錯工具會使用所產生之 catch 的 IL 位移來處理 catch，就好像它是非使用者程式碼一樣，即使它可能發生在使用者程式碼方法中也一樣。</span><span class="sxs-lookup"><span data-stu-id="9bef4-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="9bef4-105">尤其是，它是用來回應 **CatchHandlerFound** 例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="9bef4-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bef4-106">語法</span><span class="sxs-lookup"><span data-stu-id="9bef4-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bef4-107">參數</span><span class="sxs-lookup"><span data-stu-id="9bef4-107">Parameters</span></span>  
  
|<span data-ttu-id="9bef4-108">參數</span><span class="sxs-lookup"><span data-stu-id="9bef4-108">Parameter</span></span>|<span data-ttu-id="9bef4-109">描述</span><span class="sxs-lookup"><span data-stu-id="9bef4-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="9bef4-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="9bef4-110">Return Value</span></span>  

 <span data-ttu-id="9bef4-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="9bef4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bef4-112">需求</span><span class="sxs-lookup"><span data-stu-id="9bef4-112">Requirements</span></span>  

 <span data-ttu-id="9bef4-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9bef4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bef4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bef4-114">See also</span></span>

- [<span data-ttu-id="9bef4-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="9bef4-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
