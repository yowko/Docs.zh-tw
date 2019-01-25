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
ms.openlocfilehash: 8f5fc951b629a3158fc2c2d6047234fb661f3741
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494895"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="ef0f9-102">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ef0f9-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="ef0f9-103">提供方法，以取得搜尋路徑的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ef0f9-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="ef0f9-104">取得這個介面，藉由呼叫`QueryInterface`上實作的物件[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ef0f9-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef0f9-105">方法</span><span class="sxs-lookup"><span data-stu-id="ef0f9-105">Methods</span></span>  
  
|<span data-ttu-id="ef0f9-106">方法</span><span class="sxs-lookup"><span data-stu-id="ef0f9-106">Method</span></span>|<span data-ttu-id="ef0f9-107">描述</span><span class="sxs-lookup"><span data-stu-id="ef0f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef0f9-108">GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="ef0f9-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="ef0f9-109">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ef0f9-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="ef0f9-110">GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="ef0f9-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="ef0f9-111">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="ef0f9-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="ef0f9-112">GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="ef0f9-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="ef0f9-113">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="ef0f9-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef0f9-114">需求</span><span class="sxs-lookup"><span data-stu-id="ef0f9-114">Requirements</span></span>  
 <span data-ttu-id="ef0f9-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef0f9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0f9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef0f9-116">See also</span></span>
- [<span data-ttu-id="ef0f9-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="ef0f9-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
