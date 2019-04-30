---
title: ISymUnmanagedWriter5 介面
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6ed8c6e61c558a4bc9e3f92d559615ac93ecff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962335"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="cda6d-102">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="cda6d-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="cda6d-103">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="cda6d-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda6d-104">語法</span><span class="sxs-lookup"><span data-stu-id="cda6d-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="cda6d-105">方法</span><span class="sxs-lookup"><span data-stu-id="cda6d-105">Methods</span></span>  
 <span data-ttu-id="cda6d-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="cda6d-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="cda6d-107">方法</span><span class="sxs-lookup"><span data-stu-id="cda6d-107">Method</span></span>|<span data-ttu-id="cda6d-108">描述</span><span class="sxs-lookup"><span data-stu-id="cda6d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cda6d-109">CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="cda6d-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="cda6d-110">關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="cda6d-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="cda6d-111">它已關閉之後，就可以不新增任何更多的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="cda6d-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="cda6d-112">MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="cda6d-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="cda6d-113">對應至指定的原始程式檔指定的中繼資料語彙基元跨越指定的原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="cda6d-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="cda6d-114">必須呼叫之間呼叫[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)並[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)。</span><span class="sxs-lookup"><span data-stu-id="cda6d-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="cda6d-115">OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="cda6d-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="cda6d-116">開啟要發出至來源語彙基元範圍的對應資訊的特殊的自訂資料 區段。</span><span class="sxs-lookup"><span data-stu-id="cda6d-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="cda6d-117">方法已開啟，或反之亦然，會發生錯誤時，請開啟這一節。</span><span class="sxs-lookup"><span data-stu-id="cda6d-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cda6d-118">需求</span><span class="sxs-lookup"><span data-stu-id="cda6d-118">Requirements</span></span>  
 <span data-ttu-id="cda6d-119">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cda6d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda6d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cda6d-120">See also</span></span>

- [<span data-ttu-id="cda6d-121">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="cda6d-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="cda6d-122">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="cda6d-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
