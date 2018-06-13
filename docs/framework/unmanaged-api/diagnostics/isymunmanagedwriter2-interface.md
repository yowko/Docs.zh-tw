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
ms.openlocfilehash: cbafe39fffd28a9bfccaa275c9009bc03549cda6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429423"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="b5b9b-102">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="b5b9b-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="b5b9b-103">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="b5b9b-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b5b9b-104">這個介面延伸[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b5b9b-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5b9b-105">方法</span><span class="sxs-lookup"><span data-stu-id="b5b9b-105">Methods</span></span>  
  
|<span data-ttu-id="b5b9b-106">方法</span><span class="sxs-lookup"><span data-stu-id="b5b9b-106">Method</span></span>|<span data-ttu-id="b5b9b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b5b9b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5b9b-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="b5b9b-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="b5b9b-109">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="b5b9b-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="b5b9b-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="b5b9b-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="b5b9b-111">定義單一的全域變數。</span><span class="sxs-lookup"><span data-stu-id="b5b9b-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="b5b9b-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="b5b9b-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="b5b9b-113">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="b5b9b-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5b9b-114">需求</span><span class="sxs-lookup"><span data-stu-id="b5b9b-114">Requirements</span></span>  
 <span data-ttu-id="b5b9b-115">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5b9b-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b9b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5b9b-116">See Also</span></span>  
 [<span data-ttu-id="b5b9b-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="b5b9b-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="b5b9b-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b5b9b-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b5b9b-119">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="b5b9b-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
