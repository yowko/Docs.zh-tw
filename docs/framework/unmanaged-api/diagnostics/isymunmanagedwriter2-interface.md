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
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683325"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="4d7e7-102">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="4d7e7-102">ISymUnmanagedWriter2 Interface</span></span>

<span data-ttu-id="4d7e7-103">表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="4d7e7-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="4d7e7-104">這個介面會擴充 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="4d7e7-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d7e7-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d7e7-105">Methods</span></span>  
  
|<span data-ttu-id="4d7e7-106">方法</span><span class="sxs-lookup"><span data-stu-id="4d7e7-106">Method</span></span>|<span data-ttu-id="4d7e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="4d7e7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d7e7-108">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="4d7e7-108">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="4d7e7-109">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d7e7-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="4d7e7-110">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="4d7e7-110">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="4d7e7-111">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="4d7e7-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="4d7e7-112">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="4d7e7-112">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="4d7e7-113">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="4d7e7-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d7e7-114">需求</span><span class="sxs-lookup"><span data-stu-id="4d7e7-114">Requirements</span></span>  

 <span data-ttu-id="4d7e7-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="4d7e7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7e7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d7e7-116">See also</span></span>

- [<span data-ttu-id="4d7e7-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="4d7e7-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="4d7e7-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="4d7e7-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="4d7e7-119">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="4d7e7-119">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
