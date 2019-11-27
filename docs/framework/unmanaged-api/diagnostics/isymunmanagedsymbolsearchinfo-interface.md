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
ms.openlocfilehash: d7371361b074454e8aa359c49b964193c12f3034
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446143"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="27b48-102">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="27b48-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="27b48-103">提供取得搜尋路徑相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="27b48-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="27b48-104">藉由在[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面的物件上呼叫 `QueryInterface` 來取得此介面。</span><span class="sxs-lookup"><span data-stu-id="27b48-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27b48-105">方法</span><span class="sxs-lookup"><span data-stu-id="27b48-105">Methods</span></span>  
  
|<span data-ttu-id="27b48-106">方法</span><span class="sxs-lookup"><span data-stu-id="27b48-106">Method</span></span>|<span data-ttu-id="27b48-107">描述</span><span class="sxs-lookup"><span data-stu-id="27b48-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27b48-108">GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="27b48-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="27b48-109">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="27b48-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="27b48-110">GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="27b48-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="27b48-111">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="27b48-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="27b48-112">GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="27b48-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="27b48-113">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="27b48-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27b48-114">需求</span><span class="sxs-lookup"><span data-stu-id="27b48-114">Requirements</span></span>  
 <span data-ttu-id="27b48-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="27b48-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b48-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27b48-116">See also</span></span>

- [<span data-ttu-id="27b48-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="27b48-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
