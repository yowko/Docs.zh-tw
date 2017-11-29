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
ms.openlocfilehash: adcdf44582aaf801a39c9beb9831c493a9945fd0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="9609e-102">ISymUnmanagedWriter5::MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="9609e-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="9609e-103">對應至指定的原始程式行的指定中繼資料語彙基元跨越指定的原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="9609e-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="9609e-104">必須呼叫之間呼叫[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9609e-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9609e-105">語法</span><span class="sxs-lookup"><span data-stu-id="9609e-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9609e-106">參數</span><span class="sxs-lookup"><span data-stu-id="9609e-106">Parameters</span></span>  
  
|<span data-ttu-id="9609e-107">參數</span><span class="sxs-lookup"><span data-stu-id="9609e-107">Parameter</span></span>|<span data-ttu-id="9609e-108">說明</span><span class="sxs-lookup"><span data-stu-id="9609e-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="9609e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9609e-109">Return Value</span></span>  
 <span data-ttu-id="9609e-110">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="9609e-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9609e-111">需求</span><span class="sxs-lookup"><span data-stu-id="9609e-111">Requirements</span></span>  
 <span data-ttu-id="9609e-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9609e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9609e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9609e-113">See Also</span></span>  
 [<span data-ttu-id="9609e-114">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="9609e-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
