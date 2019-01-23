---
title: ISymUnmanagedWriter2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99e8b8bbb25bc55c7d4f2f44aac8e24210d30b83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560541"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="31de9-102">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="31de9-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="31de9-103">表示的符號寫入器，並提供方法，以定義文件，序列點、 語彙範圍變數。</span><span class="sxs-lookup"><span data-stu-id="31de9-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="31de9-104">這個介面會擴充[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="31de9-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31de9-105">方法</span><span class="sxs-lookup"><span data-stu-id="31de9-105">Methods</span></span>  
  
|<span data-ttu-id="31de9-106">方法</span><span class="sxs-lookup"><span data-stu-id="31de9-106">Method</span></span>|<span data-ttu-id="31de9-107">描述</span><span class="sxs-lookup"><span data-stu-id="31de9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31de9-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="31de9-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="31de9-109">定義常值的名稱。</span><span class="sxs-lookup"><span data-stu-id="31de9-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="31de9-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="31de9-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="31de9-111">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="31de9-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="31de9-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="31de9-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="31de9-113">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="31de9-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31de9-114">需求</span><span class="sxs-lookup"><span data-stu-id="31de9-114">Requirements</span></span>  
 <span data-ttu-id="31de9-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31de9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31de9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31de9-116">See also</span></span>
- [<span data-ttu-id="31de9-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="31de9-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="31de9-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="31de9-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="31de9-119">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="31de9-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
