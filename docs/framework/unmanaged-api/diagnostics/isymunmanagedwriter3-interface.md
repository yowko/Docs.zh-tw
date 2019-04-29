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
ms.openlocfilehash: e26d79a5b597b8585f2fffd7f3945f00832ca134
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650709"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="f8f48-102">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="f8f48-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="f8f48-103">表示的符號寫入器，並提供方法，以定義文件，序列點、 語彙範圍變數。</span><span class="sxs-lookup"><span data-stu-id="f8f48-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="f8f48-104">這個介面會擴充[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="f8f48-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8f48-105">方法</span><span class="sxs-lookup"><span data-stu-id="f8f48-105">Methods</span></span>  
  
|<span data-ttu-id="f8f48-106">方法</span><span class="sxs-lookup"><span data-stu-id="f8f48-106">Method</span></span>|<span data-ttu-id="f8f48-107">描述</span><span class="sxs-lookup"><span data-stu-id="f8f48-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8f48-108">Commit 方法</span><span class="sxs-lookup"><span data-stu-id="f8f48-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="f8f48-109">認可的變更寫入目前資料流。</span><span class="sxs-lookup"><span data-stu-id="f8f48-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="f8f48-110">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="f8f48-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="f8f48-111">開啟的方法，並提供映像中的實際的區段位移。</span><span class="sxs-lookup"><span data-stu-id="f8f48-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8f48-112">需求</span><span class="sxs-lookup"><span data-stu-id="f8f48-112">Requirements</span></span>  
 <span data-ttu-id="f8f48-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8f48-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f48-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8f48-114">See also</span></span>

- [<span data-ttu-id="f8f48-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="f8f48-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f8f48-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="f8f48-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="f8f48-117">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="f8f48-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
