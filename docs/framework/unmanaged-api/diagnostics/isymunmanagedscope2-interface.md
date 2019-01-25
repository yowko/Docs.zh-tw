---
title: ISymUnmanagedScope2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb48835039f142ea1d9e18871f77ada1b6f4f3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706309"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="3e0b4-102">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="3e0b4-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="3e0b4-103">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="3e0b4-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="3e0b4-104">這個介面會擴充[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面與方法，以取得關於常數所定義的範圍內。</span><span class="sxs-lookup"><span data-stu-id="3e0b4-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e0b4-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e0b4-105">Methods</span></span>  
  
|<span data-ttu-id="3e0b4-106">方法</span><span class="sxs-lookup"><span data-stu-id="3e0b4-106">Method</span></span>|<span data-ttu-id="3e0b4-107">描述</span><span class="sxs-lookup"><span data-stu-id="3e0b4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e0b4-108">GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="3e0b4-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="3e0b4-109">取得此範圍內所定義的計數。</span><span class="sxs-lookup"><span data-stu-id="3e0b4-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="3e0b4-110">GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="3e0b4-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="3e0b4-111">取得此範圍內定義的區域常數。</span><span class="sxs-lookup"><span data-stu-id="3e0b4-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e0b4-112">需求</span><span class="sxs-lookup"><span data-stu-id="3e0b4-112">Requirements</span></span>  
 <span data-ttu-id="3e0b4-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3e0b4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e0b4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e0b4-114">See also</span></span>
- [<span data-ttu-id="3e0b4-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="3e0b4-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3e0b4-116">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="3e0b4-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
