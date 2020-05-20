---
title: ISymUnmanagedSymbolSearchInfo 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610661"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="ffc39-102">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ffc39-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="ffc39-103">提供取得搜尋路徑相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="ffc39-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="ffc39-104">`QueryInterface`在執行[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得此介面。</span><span class="sxs-lookup"><span data-stu-id="ffc39-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffc39-105">方法</span><span class="sxs-lookup"><span data-stu-id="ffc39-105">Methods</span></span>  
  
|<span data-ttu-id="ffc39-106">方法</span><span class="sxs-lookup"><span data-stu-id="ffc39-106">Method</span></span>|<span data-ttu-id="ffc39-107">描述</span><span class="sxs-lookup"><span data-stu-id="ffc39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffc39-108">GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="ffc39-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="ffc39-109">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ffc39-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="ffc39-110">GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="ffc39-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="ffc39-111">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="ffc39-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="ffc39-112">GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="ffc39-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="ffc39-113">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="ffc39-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ffc39-114">需求</span><span class="sxs-lookup"><span data-stu-id="ffc39-114">Requirements</span></span>  
 <span data-ttu-id="ffc39-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ffc39-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc39-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffc39-116">See also</span></span>

- [<span data-ttu-id="ffc39-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="ffc39-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
