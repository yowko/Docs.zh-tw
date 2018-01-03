---
title: "ISymUnmanagedSymbolSearchInfo 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo
helpviewer_keywords: ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 441330471906a891646ad55eb73ec25b44800cbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="fc1e6-102">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fc1e6-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="fc1e6-103">提供方法，以取得搜尋路徑的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fc1e6-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="fc1e6-104">取得此介面，藉由呼叫`QueryInterface`實作的物件上[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="fc1e6-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc1e6-105">方法</span><span class="sxs-lookup"><span data-stu-id="fc1e6-105">Methods</span></span>  
  
|<span data-ttu-id="fc1e6-106">方法</span><span class="sxs-lookup"><span data-stu-id="fc1e6-106">Method</span></span>|<span data-ttu-id="fc1e6-107">描述</span><span class="sxs-lookup"><span data-stu-id="fc1e6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc1e6-108">GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="fc1e6-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="fc1e6-109">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="fc1e6-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="fc1e6-110">GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="fc1e6-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="fc1e6-111">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="fc1e6-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="fc1e6-112">GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="fc1e6-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="fc1e6-113">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="fc1e6-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc1e6-114">需求</span><span class="sxs-lookup"><span data-stu-id="fc1e6-114">Requirements</span></span>  
 <span data-ttu-id="fc1e6-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc1e6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1e6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc1e6-116">See Also</span></span>  
 [<span data-ttu-id="fc1e6-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="fc1e6-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
