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
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="051e6-102">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="051e6-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="051e6-103">Represents a lexical scope within a method.</span><span class="sxs-lookup"><span data-stu-id="051e6-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="051e6-104">方法</span><span class="sxs-lookup"><span data-stu-id="051e6-104">Methods</span></span>  
  
|<span data-ttu-id="051e6-105">方法</span><span class="sxs-lookup"><span data-stu-id="051e6-105">Method</span></span>|<span data-ttu-id="051e6-106">描述</span><span class="sxs-lookup"><span data-stu-id="051e6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="051e6-107">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="051e6-108">Gets the children of this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="051e6-109">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="051e6-110">Gets the end offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="051e6-111">GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="051e6-112">Gets a count of the local variables defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="051e6-113">GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="051e6-114">Gets the local variables defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="051e6-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="051e6-116">Gets the method that contains this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="051e6-117">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="051e6-118">Gets the namespaces that are being used within this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="051e6-119">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="051e6-120">Gets the parent scope of this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="051e6-121">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="051e6-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="051e6-122">Gets the start offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="051e6-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="051e6-123">需求</span><span class="sxs-lookup"><span data-stu-id="051e6-123">Requirements</span></span>  
 <span data-ttu-id="051e6-124">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="051e6-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051e6-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="051e6-125">See also</span></span>

- [<span data-ttu-id="051e6-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="051e6-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="051e6-127">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="051e6-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
