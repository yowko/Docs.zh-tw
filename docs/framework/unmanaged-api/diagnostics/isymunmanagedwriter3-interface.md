---
title: ISymUnmanagedWriter3 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1315d54e93769772772d536e9688c754a96c67c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429390"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="b487d-102">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="b487d-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="b487d-103">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="b487d-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b487d-104">這個介面延伸[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b487d-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b487d-105">方法</span><span class="sxs-lookup"><span data-stu-id="b487d-105">Methods</span></span>  
  
|<span data-ttu-id="b487d-106">方法</span><span class="sxs-lookup"><span data-stu-id="b487d-106">Method</span></span>|<span data-ttu-id="b487d-107">描述</span><span class="sxs-lookup"><span data-stu-id="b487d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b487d-108">Commit 方法</span><span class="sxs-lookup"><span data-stu-id="b487d-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="b487d-109">認可的變更寫入目前資料流。</span><span class="sxs-lookup"><span data-stu-id="b487d-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="b487d-110">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="b487d-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="b487d-111">開啟的方法，並提供其實際的區段位移，映像中。</span><span class="sxs-lookup"><span data-stu-id="b487d-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b487d-112">需求</span><span class="sxs-lookup"><span data-stu-id="b487d-112">Requirements</span></span>  
 <span data-ttu-id="b487d-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b487d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b487d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b487d-114">See Also</span></span>  
 [<span data-ttu-id="b487d-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="b487d-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b487d-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b487d-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b487d-117">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="b487d-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
