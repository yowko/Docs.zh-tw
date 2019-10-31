---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan 方法
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 876804e7b825443116b1f44a02a685a73153915c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121630"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="2896b-102">ISymUnmanagedWriter5::MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="2896b-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="2896b-103">將給定的元資料標記對應至指定之原始程式檔中的給定原始程式列範圍。</span><span class="sxs-lookup"><span data-stu-id="2896b-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="2896b-104">必須在[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)的呼叫之間呼叫。</span><span class="sxs-lookup"><span data-stu-id="2896b-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2896b-105">語法</span><span class="sxs-lookup"><span data-stu-id="2896b-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2896b-106">參數</span><span class="sxs-lookup"><span data-stu-id="2896b-106">Parameters</span></span>  
  
|<span data-ttu-id="2896b-107">參數</span><span class="sxs-lookup"><span data-stu-id="2896b-107">Parameter</span></span>|<span data-ttu-id="2896b-108">描述</span><span class="sxs-lookup"><span data-stu-id="2896b-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="2896b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="2896b-109">Return Value</span></span>  
 <span data-ttu-id="2896b-110">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="2896b-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2896b-111">需求</span><span class="sxs-lookup"><span data-stu-id="2896b-111">Requirements</span></span>  
 <span data-ttu-id="2896b-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2896b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2896b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="2896b-113">See also</span></span>

- [<span data-ttu-id="2896b-114">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="2896b-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
