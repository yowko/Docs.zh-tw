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
ms.openlocfilehash: 95ad3cbea4269173f22e662d15772ff97f7ee900
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705445"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="412ac-102">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="412ac-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>

<span data-ttu-id="412ac-103">提供可取得搜尋路徑相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="412ac-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="412ac-104">`QueryInterface`在實[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得這個介面。</span><span class="sxs-lookup"><span data-stu-id="412ac-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="412ac-105">方法</span><span class="sxs-lookup"><span data-stu-id="412ac-105">Methods</span></span>  
  
|<span data-ttu-id="412ac-106">方法</span><span class="sxs-lookup"><span data-stu-id="412ac-106">Method</span></span>|<span data-ttu-id="412ac-107">描述</span><span class="sxs-lookup"><span data-stu-id="412ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="412ac-108">GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="412ac-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="412ac-109">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="412ac-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="412ac-110">GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="412ac-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="412ac-111">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="412ac-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="412ac-112">GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="412ac-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="412ac-113">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="412ac-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="412ac-114">需求</span><span class="sxs-lookup"><span data-stu-id="412ac-114">Requirements</span></span>  

 <span data-ttu-id="412ac-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="412ac-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="412ac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="412ac-116">See also</span></span>

- [<span data-ttu-id="412ac-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="412ac-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
