---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan 方法
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501673"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="d35d5-102">ISymUnmanagedWriter5::MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="d35d5-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="d35d5-103">將給定的元資料標記對應至指定之原始程式檔中的給定原始程式列範圍。</span><span class="sxs-lookup"><span data-stu-id="d35d5-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="d35d5-104">必須在[OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)的呼叫之間呼叫。</span><span class="sxs-lookup"><span data-stu-id="d35d5-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35d5-105">語法</span><span class="sxs-lookup"><span data-stu-id="d35d5-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d35d5-106">參數</span><span class="sxs-lookup"><span data-stu-id="d35d5-106">Parameters</span></span>  
  
|<span data-ttu-id="d35d5-107">參數</span><span class="sxs-lookup"><span data-stu-id="d35d5-107">Parameter</span></span>|<span data-ttu-id="d35d5-108">說明</span><span class="sxs-lookup"><span data-stu-id="d35d5-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="d35d5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d35d5-109">Return Value</span></span>  
 <span data-ttu-id="d35d5-110">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="d35d5-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35d5-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="d35d5-111">Requirements</span></span>  
 <span data-ttu-id="d35d5-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d35d5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35d5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d35d5-113">See also</span></span>

- [<span data-ttu-id="d35d5-114">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="d35d5-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
