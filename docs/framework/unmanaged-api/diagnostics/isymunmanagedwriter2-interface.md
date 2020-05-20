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
ms.openlocfilehash: 1fe6055d930c6d30e947d6bc774d0520a9e175ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614678"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="1b44e-102">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="1b44e-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="1b44e-103">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="1b44e-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="1b44e-104">這個介面會擴充[ISymUnmanagedWriter](isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="1b44e-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b44e-105">方法</span><span class="sxs-lookup"><span data-stu-id="1b44e-105">Methods</span></span>  
  
|<span data-ttu-id="1b44e-106">方法</span><span class="sxs-lookup"><span data-stu-id="1b44e-106">Method</span></span>|<span data-ttu-id="1b44e-107">描述</span><span class="sxs-lookup"><span data-stu-id="1b44e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b44e-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="1b44e-108">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="1b44e-109">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b44e-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="1b44e-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="1b44e-110">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="1b44e-111">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="1b44e-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="1b44e-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="1b44e-112">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="1b44e-113">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="1b44e-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b44e-114">需求</span><span class="sxs-lookup"><span data-stu-id="1b44e-114">Requirements</span></span>  
 <span data-ttu-id="1b44e-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="1b44e-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b44e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b44e-116">See also</span></span>

- [<span data-ttu-id="1b44e-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="1b44e-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="1b44e-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="1b44e-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="1b44e-119">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="1b44e-119">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
