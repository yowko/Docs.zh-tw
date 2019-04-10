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
ms.openlocfilehash: 2a872774b1c4510c8d0325c59ae7678c867c1aff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216804"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="ca49f-102">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ca49f-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="ca49f-103">提供方法，以取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="ca49f-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="ca49f-104">取得這個介面，藉由呼叫`QueryInterface`上實作的物件[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ca49f-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca49f-105">方法</span><span class="sxs-lookup"><span data-stu-id="ca49f-105">Methods</span></span>  
  
|<span data-ttu-id="ca49f-106">方法</span><span class="sxs-lookup"><span data-stu-id="ca49f-106">Method</span></span>|<span data-ttu-id="ca49f-107">描述</span><span class="sxs-lookup"><span data-stu-id="ca49f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca49f-108">GetSymbolSearchInfo 方法</span><span class="sxs-lookup"><span data-stu-id="ca49f-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="ca49f-109">取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="ca49f-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="ca49f-110">GetSymbolSearchInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="ca49f-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="ca49f-111">取得符號搜尋資訊的計數。</span><span class="sxs-lookup"><span data-stu-id="ca49f-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca49f-112">需求</span><span class="sxs-lookup"><span data-stu-id="ca49f-112">Requirements</span></span>  
 <span data-ttu-id="ca49f-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca49f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca49f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca49f-114">See also</span></span>

- [<span data-ttu-id="ca49f-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="ca49f-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
