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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d573264bb7a3cac02dd41afacaa2bc4a6f9e6dcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207541"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="0e613-102">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="0e613-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="0e613-103">提供方法，以取得搜尋路徑的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0e613-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="0e613-104">取得這個介面，藉由呼叫`QueryInterface`上實作的物件[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="0e613-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e613-105">方法</span><span class="sxs-lookup"><span data-stu-id="0e613-105">Methods</span></span>  
  
|<span data-ttu-id="0e613-106">方法</span><span class="sxs-lookup"><span data-stu-id="0e613-106">Method</span></span>|<span data-ttu-id="0e613-107">描述</span><span class="sxs-lookup"><span data-stu-id="0e613-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e613-108">GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="0e613-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="0e613-109">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="0e613-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="0e613-110">GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="0e613-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="0e613-111">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="0e613-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="0e613-112">GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="0e613-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="0e613-113">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="0e613-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e613-114">需求</span><span class="sxs-lookup"><span data-stu-id="0e613-114">Requirements</span></span>  
 <span data-ttu-id="0e613-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0e613-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e613-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e613-116">See also</span></span>

- [<span data-ttu-id="0e613-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="0e613-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
