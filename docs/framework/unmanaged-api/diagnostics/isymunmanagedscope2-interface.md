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
ms.openlocfilehash: 3374097c8d343fed6badf046742ca556d2a92f3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446224"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="fd963-102">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="fd963-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="fd963-103">Represents a lexical scope within a method.</span><span class="sxs-lookup"><span data-stu-id="fd963-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="fd963-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span><span class="sxs-lookup"><span data-stu-id="fd963-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd963-105">方法</span><span class="sxs-lookup"><span data-stu-id="fd963-105">Methods</span></span>  
  
|<span data-ttu-id="fd963-106">方法</span><span class="sxs-lookup"><span data-stu-id="fd963-106">Method</span></span>|<span data-ttu-id="fd963-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd963-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd963-108">GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="fd963-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="fd963-109">Gets a count of the constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="fd963-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="fd963-110">GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="fd963-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="fd963-111">Gets the local constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="fd963-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd963-112">需求</span><span class="sxs-lookup"><span data-stu-id="fd963-112">Requirements</span></span>  
 <span data-ttu-id="fd963-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd963-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd963-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd963-114">See also</span></span>

- [<span data-ttu-id="fd963-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="fd963-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fd963-116">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="fd963-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
