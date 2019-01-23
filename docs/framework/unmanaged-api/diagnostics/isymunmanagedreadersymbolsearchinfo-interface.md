---
title: ISymUnmanagedReaderSymbolSearchInfo 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6eb99de44c2d3f1afe6dda2d6ec895ec57c617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634997"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="17cc8-102">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="17cc8-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="17cc8-103">提供方法，以取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="17cc8-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="17cc8-104">取得這個介面，藉由呼叫`QueryInterface`上實作的物件[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="17cc8-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17cc8-105">方法</span><span class="sxs-lookup"><span data-stu-id="17cc8-105">Methods</span></span>  
  
|<span data-ttu-id="17cc8-106">方法</span><span class="sxs-lookup"><span data-stu-id="17cc8-106">Method</span></span>|<span data-ttu-id="17cc8-107">描述</span><span class="sxs-lookup"><span data-stu-id="17cc8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17cc8-108">GetSymbolSearchInfo 方法</span><span class="sxs-lookup"><span data-stu-id="17cc8-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="17cc8-109">取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="17cc8-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="17cc8-110">GetSymbolSearchInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="17cc8-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="17cc8-111">取得符號搜尋資訊的計數。</span><span class="sxs-lookup"><span data-stu-id="17cc8-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17cc8-112">需求</span><span class="sxs-lookup"><span data-stu-id="17cc8-112">Requirements</span></span>  
 <span data-ttu-id="17cc8-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="17cc8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cc8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17cc8-114">See also</span></span>
- [<span data-ttu-id="17cc8-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="17cc8-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
