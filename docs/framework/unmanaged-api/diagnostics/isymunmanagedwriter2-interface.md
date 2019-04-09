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
ms.openlocfilehash: 97df6d6ec9a446e89eef8a9f8a5e5e8ddc85c0f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127396"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="6c93d-102">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="6c93d-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="6c93d-103">表示的符號寫入器，並提供方法，以定義文件，序列點、 語彙範圍變數。</span><span class="sxs-lookup"><span data-stu-id="6c93d-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="6c93d-104">這個介面會擴充[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="6c93d-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c93d-105">方法</span><span class="sxs-lookup"><span data-stu-id="6c93d-105">Methods</span></span>  
  
|<span data-ttu-id="6c93d-106">方法</span><span class="sxs-lookup"><span data-stu-id="6c93d-106">Method</span></span>|<span data-ttu-id="6c93d-107">描述</span><span class="sxs-lookup"><span data-stu-id="6c93d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c93d-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="6c93d-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="6c93d-109">定義常值的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c93d-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="6c93d-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="6c93d-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="6c93d-111">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="6c93d-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="6c93d-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="6c93d-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="6c93d-113">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="6c93d-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c93d-114">需求</span><span class="sxs-lookup"><span data-stu-id="6c93d-114">Requirements</span></span>  
 <span data-ttu-id="6c93d-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c93d-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c93d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c93d-116">See also</span></span>

- [<span data-ttu-id="6c93d-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="6c93d-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="6c93d-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="6c93d-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="6c93d-119">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="6c93d-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
