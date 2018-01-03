---
title: "ISymUnmanagedWriter5::MapTokenToSourceSpan 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad40258b0fd562babb5e395ddbd05eca23e21ffe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="3bed4-102">ISymUnmanagedWriter5::MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="3bed4-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="3bed4-103">對應至指定的原始程式行的指定中繼資料語彙基元跨越指定的原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="3bed4-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="3bed4-104">必須呼叫之間呼叫[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3bed4-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bed4-105">語法</span><span class="sxs-lookup"><span data-stu-id="3bed4-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bed4-106">參數</span><span class="sxs-lookup"><span data-stu-id="3bed4-106">Parameters</span></span>  
  
|<span data-ttu-id="3bed4-107">參數</span><span class="sxs-lookup"><span data-stu-id="3bed4-107">Parameter</span></span>|<span data-ttu-id="3bed4-108">描述</span><span class="sxs-lookup"><span data-stu-id="3bed4-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="3bed4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3bed4-109">Return Value</span></span>  
 <span data-ttu-id="3bed4-110">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="3bed4-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bed4-111">需求</span><span class="sxs-lookup"><span data-stu-id="3bed4-111">Requirements</span></span>  
 <span data-ttu-id="3bed4-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3bed4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bed4-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3bed4-113">See Also</span></span>  
 [<span data-ttu-id="3bed4-114">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="3bed4-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
