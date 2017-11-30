---
title: "ISymUnmanagedScope 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope
helpviewer_keywords: ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d25d62dd42e3e93124c9a3bd8945be265f192663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="adf11-102">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="adf11-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="adf11-103">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="adf11-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adf11-104">方法</span><span class="sxs-lookup"><span data-stu-id="adf11-104">Methods</span></span>  
  
|<span data-ttu-id="adf11-105">方法</span><span class="sxs-lookup"><span data-stu-id="adf11-105">Method</span></span>|<span data-ttu-id="adf11-106">說明</span><span class="sxs-lookup"><span data-stu-id="adf11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adf11-107">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="adf11-108">取得此領域的子系。</span><span class="sxs-lookup"><span data-stu-id="adf11-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="adf11-109">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="adf11-110">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="adf11-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="adf11-111">GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="adf11-112">取得此範圍內定義的本機變數的計數。</span><span class="sxs-lookup"><span data-stu-id="adf11-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="adf11-113">GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="adf11-114">取得此範圍內定義的本機變數。</span><span class="sxs-lookup"><span data-stu-id="adf11-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="adf11-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="adf11-116">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="adf11-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="adf11-117">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="adf11-118">取得此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="adf11-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="adf11-119">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="adf11-120">取得此範圍的父範圍。</span><span class="sxs-lookup"><span data-stu-id="adf11-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="adf11-121">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="adf11-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="adf11-122">取得此範圍的起始位移。</span><span class="sxs-lookup"><span data-stu-id="adf11-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adf11-123">需求</span><span class="sxs-lookup"><span data-stu-id="adf11-123">Requirements</span></span>  
 <span data-ttu-id="adf11-124">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="adf11-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf11-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adf11-125">See Also</span></span>  
 [<span data-ttu-id="adf11-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="adf11-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="adf11-127">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="adf11-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
