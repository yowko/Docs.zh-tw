---
title: "ISymUnmanagedWriter5 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="b3245-102">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="b3245-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="b3245-103">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="b3245-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3245-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3245-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="b3245-105">方法</span><span class="sxs-lookup"><span data-stu-id="b3245-105">Methods</span></span>  
 <span data-ttu-id="b3245-106">這個介面包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="b3245-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="b3245-107">方法</span><span class="sxs-lookup"><span data-stu-id="b3245-107">Method</span></span>|<span data-ttu-id="b3245-108">說明</span><span class="sxs-lookup"><span data-stu-id="b3245-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3245-109">CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="b3245-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="b3245-110">關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="b3245-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="b3245-111">它已關閉之後，就可以加入沒有對應的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b3245-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="b3245-112">MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="b3245-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="b3245-113">對應至指定的原始程式行的指定中繼資料語彙基元跨越指定的原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="b3245-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="b3245-114">必須呼叫之間呼叫[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b3245-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="b3245-115">OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="b3245-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="b3245-116">開啟發出到語彙基元至來源範圍的對應資訊的特殊的自訂資料區段。</span><span class="sxs-lookup"><span data-stu-id="b3245-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="b3245-117">方法已經開啟，或反之亦然，會發生錯誤時，請開啟此區段。</span><span class="sxs-lookup"><span data-stu-id="b3245-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3245-118">需求</span><span class="sxs-lookup"><span data-stu-id="b3245-118">Requirements</span></span>  
 <span data-ttu-id="b3245-119">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b3245-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3245-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3245-120">See Also</span></span>  
 [<span data-ttu-id="b3245-121">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="b3245-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b3245-122">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="b3245-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
