---
title: "ISymUnmanagedScope2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f6d2ec846a34b2d3424f7bf8b54f1d4d12d4102e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="e0a7a-102">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="e0a7a-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="e0a7a-103">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="e0a7a-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="e0a7a-104">這個介面延伸[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面與方法，以取得關於常數所定義的範圍內。</span><span class="sxs-lookup"><span data-stu-id="e0a7a-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0a7a-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0a7a-105">Methods</span></span>  
  
|<span data-ttu-id="e0a7a-106">方法</span><span class="sxs-lookup"><span data-stu-id="e0a7a-106">Method</span></span>|<span data-ttu-id="e0a7a-107">描述</span><span class="sxs-lookup"><span data-stu-id="e0a7a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0a7a-108">GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="e0a7a-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="e0a7a-109">取得此範圍內定義的常數的計數。</span><span class="sxs-lookup"><span data-stu-id="e0a7a-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="e0a7a-110">GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="e0a7a-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="e0a7a-111">取得定義在這個範圍內的區域常數。</span><span class="sxs-lookup"><span data-stu-id="e0a7a-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0a7a-112">需求</span><span class="sxs-lookup"><span data-stu-id="e0a7a-112">Requirements</span></span>  
 <span data-ttu-id="e0a7a-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e0a7a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a7a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0a7a-114">See Also</span></span>  
 [<span data-ttu-id="e0a7a-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="e0a7a-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="e0a7a-116">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="e0a7a-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
