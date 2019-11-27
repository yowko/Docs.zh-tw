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
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446259"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="d399c-102">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="d399c-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="d399c-103">表示方法內的詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="d399c-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d399c-104">方法</span><span class="sxs-lookup"><span data-stu-id="d399c-104">Methods</span></span>  
  
|<span data-ttu-id="d399c-105">方法</span><span class="sxs-lookup"><span data-stu-id="d399c-105">Method</span></span>|<span data-ttu-id="d399c-106">描述</span><span class="sxs-lookup"><span data-stu-id="d399c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d399c-107">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="d399c-108">取得此範圍的子系。</span><span class="sxs-lookup"><span data-stu-id="d399c-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="d399c-109">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="d399c-110">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="d399c-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="d399c-111">GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="d399c-112">取得在此範圍內定義的區域變數計數。</span><span class="sxs-lookup"><span data-stu-id="d399c-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="d399c-113">GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="d399c-114">取得在此範圍內定義的區域變數。</span><span class="sxs-lookup"><span data-stu-id="d399c-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="d399c-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="d399c-116">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="d399c-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="d399c-117">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="d399c-118">取得在此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d399c-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="d399c-119">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="d399c-120">取得此範圍的父範圍。</span><span class="sxs-lookup"><span data-stu-id="d399c-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="d399c-121">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d399c-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="d399c-122">取得此範圍的開始位移。</span><span class="sxs-lookup"><span data-stu-id="d399c-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d399c-123">需求</span><span class="sxs-lookup"><span data-stu-id="d399c-123">Requirements</span></span>  
 <span data-ttu-id="d399c-124">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d399c-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d399c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d399c-125">See also</span></span>

- [<span data-ttu-id="d399c-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d399c-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d399c-127">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="d399c-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
