---
title: "ISymUnmanagedWriter2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2
helpviewer_keywords: ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98461cd2c2bc26d78f3f3f747b95d46576ba01e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="d68e5-102">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="d68e5-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="d68e5-103">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="d68e5-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d68e5-104">這個介面延伸[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="d68e5-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d68e5-105">方法</span><span class="sxs-lookup"><span data-stu-id="d68e5-105">Methods</span></span>  
  
|<span data-ttu-id="d68e5-106">方法</span><span class="sxs-lookup"><span data-stu-id="d68e5-106">Method</span></span>|<span data-ttu-id="d68e5-107">描述</span><span class="sxs-lookup"><span data-stu-id="d68e5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d68e5-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="d68e5-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="d68e5-109">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="d68e5-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="d68e5-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="d68e5-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="d68e5-111">定義單一的全域變數。</span><span class="sxs-lookup"><span data-stu-id="d68e5-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="d68e5-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="d68e5-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="d68e5-113">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="d68e5-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d68e5-114">需求</span><span class="sxs-lookup"><span data-stu-id="d68e5-114">Requirements</span></span>  
 <span data-ttu-id="d68e5-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d68e5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68e5-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d68e5-116">See Also</span></span>  
 [<span data-ttu-id="d68e5-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d68e5-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="d68e5-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d68e5-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="d68e5-119">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="d68e5-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
