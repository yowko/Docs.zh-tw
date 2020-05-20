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
ms.openlocfilehash: 1ee406c97fa4ccb7f87098cba2925568d8ce069f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615341"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="c7761-102">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="c7761-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="c7761-103">表示方法內的詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="c7761-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7761-104">方法</span><span class="sxs-lookup"><span data-stu-id="c7761-104">Methods</span></span>  
  
|<span data-ttu-id="c7761-105">方法</span><span class="sxs-lookup"><span data-stu-id="c7761-105">Method</span></span>|<span data-ttu-id="c7761-106">描述</span><span class="sxs-lookup"><span data-stu-id="c7761-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7761-107">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-107">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="c7761-108">取得此範圍的子系。</span><span class="sxs-lookup"><span data-stu-id="c7761-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="c7761-109">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-109">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="c7761-110">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="c7761-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="c7761-111">GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-111">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="c7761-112">取得在此範圍內定義的區域變數計數。</span><span class="sxs-lookup"><span data-stu-id="c7761-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="c7761-113">GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-113">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="c7761-114">取得在此範圍內定義的區域變數。</span><span class="sxs-lookup"><span data-stu-id="c7761-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="c7761-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-115">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="c7761-116">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="c7761-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="c7761-117">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-117">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="c7761-118">取得在此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c7761-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="c7761-119">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-119">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="c7761-120">取得此範圍的父範圍。</span><span class="sxs-lookup"><span data-stu-id="c7761-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="c7761-121">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c7761-121">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="c7761-122">取得此範圍的開始位移。</span><span class="sxs-lookup"><span data-stu-id="c7761-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7761-123">需求</span><span class="sxs-lookup"><span data-stu-id="c7761-123">Requirements</span></span>  
 <span data-ttu-id="c7761-124">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c7761-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7761-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7761-125">See also</span></span>

- [<span data-ttu-id="c7761-126">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="c7761-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c7761-127">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="c7761-127">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
