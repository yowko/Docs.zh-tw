---
title: ISymUnmanagedScope 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 809368ea19528a7ce00d4fcada06ef5724eb79a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228155"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="f4ed5-102">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="f4ed5-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="f4ed5-103">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4ed5-104">方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-104">Methods</span></span>  
  
|<span data-ttu-id="f4ed5-105">方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-105">Method</span></span>|<span data-ttu-id="f4ed5-106">描述</span><span class="sxs-lookup"><span data-stu-id="f4ed5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4ed5-107">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="f4ed5-108">取得此領域的子系。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-109">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="f4ed5-110">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-111">GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="f4ed5-112">取得此範圍內定義的本機變數的計數。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-113">GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="f4ed5-114">取得此範圍內定義的本機變數。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="f4ed5-116">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-117">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="f4ed5-118">取得此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-119">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="f4ed5-120">取得此範圍的父範圍。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="f4ed5-121">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f4ed5-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="f4ed5-122">取得此範圍的開始位移。</span><span class="sxs-lookup"><span data-stu-id="f4ed5-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4ed5-123">需求</span><span class="sxs-lookup"><span data-stu-id="f4ed5-123">Requirements</span></span>  
 <span data-ttu-id="f4ed5-124">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f4ed5-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ed5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4ed5-125">See also</span></span>

- [<span data-ttu-id="f4ed5-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="f4ed5-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f4ed5-127">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="f4ed5-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
