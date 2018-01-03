---
title: "ISymUnmanagedWriter3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3
helpviewer_keywords: ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49928044bcf2c598cdc0e4315d569f2c4eb02f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="c5091-102">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="c5091-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="c5091-103">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="c5091-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c5091-104">這個介面延伸[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c5091-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5091-105">方法</span><span class="sxs-lookup"><span data-stu-id="c5091-105">Methods</span></span>  
  
|<span data-ttu-id="c5091-106">方法</span><span class="sxs-lookup"><span data-stu-id="c5091-106">Method</span></span>|<span data-ttu-id="c5091-107">描述</span><span class="sxs-lookup"><span data-stu-id="c5091-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5091-108">Commit 方法</span><span class="sxs-lookup"><span data-stu-id="c5091-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="c5091-109">認可的變更寫入目前資料流。</span><span class="sxs-lookup"><span data-stu-id="c5091-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="c5091-110">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="c5091-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="c5091-111">開啟的方法，並提供其實際的區段位移，映像中。</span><span class="sxs-lookup"><span data-stu-id="c5091-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5091-112">需求</span><span class="sxs-lookup"><span data-stu-id="c5091-112">Requirements</span></span>  
 <span data-ttu-id="c5091-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5091-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5091-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5091-114">See Also</span></span>  
 [<span data-ttu-id="c5091-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="c5091-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="c5091-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c5091-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="c5091-117">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="c5091-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
