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
ms.openlocfilehash: 40c437e109eaa4352a83c5566185593cbc6b0eba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725829"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="2e5d0-102">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="2e5d0-102">ISymUnmanagedScope2 Interface</span></span>

<span data-ttu-id="2e5d0-103">表示方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="2e5d0-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="2e5d0-104">這個介面會使用方法來擴充 [ISymUnmanagedScope](isymunmanagedscope-interface.md) 介面，以取得範圍內所定義之常數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2e5d0-104">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e5d0-105">方法</span><span class="sxs-lookup"><span data-stu-id="2e5d0-105">Methods</span></span>  
  
|<span data-ttu-id="2e5d0-106">方法</span><span class="sxs-lookup"><span data-stu-id="2e5d0-106">Method</span></span>|<span data-ttu-id="2e5d0-107">描述</span><span class="sxs-lookup"><span data-stu-id="2e5d0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e5d0-108">GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="2e5d0-108">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="2e5d0-109">取得在此範圍內定義之常數的計數。</span><span class="sxs-lookup"><span data-stu-id="2e5d0-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="2e5d0-110">GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="2e5d0-110">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="2e5d0-111">取得在此範圍內定義的本機常數。</span><span class="sxs-lookup"><span data-stu-id="2e5d0-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e5d0-112">需求</span><span class="sxs-lookup"><span data-stu-id="2e5d0-112">Requirements</span></span>  

 <span data-ttu-id="2e5d0-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2e5d0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5d0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e5d0-114">See also</span></span>

- [<span data-ttu-id="2e5d0-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="2e5d0-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="2e5d0-116">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="2e5d0-116">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
