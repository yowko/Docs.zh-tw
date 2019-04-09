---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan 方法
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08c219dd033b39fc07159875b184cdf70e3aa3ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181515"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="cbca9-102">ISymUnmanagedWriter5::MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="cbca9-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="cbca9-103">對應至指定的原始程式檔指定的中繼資料語彙基元跨越指定的原始程式檔中。</span><span class="sxs-lookup"><span data-stu-id="cbca9-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="cbca9-104">必須呼叫之間呼叫[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)並[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)。</span><span class="sxs-lookup"><span data-stu-id="cbca9-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbca9-105">語法</span><span class="sxs-lookup"><span data-stu-id="cbca9-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbca9-106">參數</span><span class="sxs-lookup"><span data-stu-id="cbca9-106">Parameters</span></span>  
  
|<span data-ttu-id="cbca9-107">參數</span><span class="sxs-lookup"><span data-stu-id="cbca9-107">Parameter</span></span>|<span data-ttu-id="cbca9-108">描述</span><span class="sxs-lookup"><span data-stu-id="cbca9-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="cbca9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cbca9-109">Return Value</span></span>  
 <span data-ttu-id="cbca9-110">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="cbca9-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbca9-111">需求</span><span class="sxs-lookup"><span data-stu-id="cbca9-111">Requirements</span></span>  
 <span data-ttu-id="cbca9-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cbca9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbca9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbca9-113">See also</span></span>

- [<span data-ttu-id="cbca9-114">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="cbca9-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
