---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan 方法
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: e4b09e6d89b3ba8ba3bf7e149d31a14a74b945b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723931"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="42baa-102">ISymUnmanagedWriter5::MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="42baa-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>

<span data-ttu-id="42baa-103">將指定的元資料標記對應至指定原始程式檔中的指定原始程式列範圍。</span><span class="sxs-lookup"><span data-stu-id="42baa-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="42baa-104">必須在呼叫 [OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) 和 [CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)之間呼叫。</span><span class="sxs-lookup"><span data-stu-id="42baa-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42baa-105">語法</span><span class="sxs-lookup"><span data-stu-id="42baa-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42baa-106">參數</span><span class="sxs-lookup"><span data-stu-id="42baa-106">Parameters</span></span>  
  
|<span data-ttu-id="42baa-107">參數</span><span class="sxs-lookup"><span data-stu-id="42baa-107">Parameter</span></span>|<span data-ttu-id="42baa-108">描述</span><span class="sxs-lookup"><span data-stu-id="42baa-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="42baa-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="42baa-109">Return Value</span></span>  

 <span data-ttu-id="42baa-110">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="42baa-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42baa-111">需求</span><span class="sxs-lookup"><span data-stu-id="42baa-111">Requirements</span></span>  

 <span data-ttu-id="42baa-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="42baa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42baa-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42baa-113">See also</span></span>

- [<span data-ttu-id="42baa-114">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="42baa-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
