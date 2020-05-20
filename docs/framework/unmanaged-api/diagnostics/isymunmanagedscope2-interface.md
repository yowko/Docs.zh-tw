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
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610856"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="eab5b-102">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="eab5b-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="eab5b-103">表示方法內的詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="eab5b-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="eab5b-104">這個介面會使用可取得範圍內所定義常數相關資訊的方法來擴充[ISymUnmanagedScope](isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="eab5b-104">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eab5b-105">方法</span><span class="sxs-lookup"><span data-stu-id="eab5b-105">Methods</span></span>  
  
|<span data-ttu-id="eab5b-106">方法</span><span class="sxs-lookup"><span data-stu-id="eab5b-106">Method</span></span>|<span data-ttu-id="eab5b-107">描述</span><span class="sxs-lookup"><span data-stu-id="eab5b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eab5b-108">GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="eab5b-108">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="eab5b-109">取得在此範圍內定義的常數計數。</span><span class="sxs-lookup"><span data-stu-id="eab5b-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="eab5b-110">GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="eab5b-110">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="eab5b-111">取得在此範圍內定義的本機常數。</span><span class="sxs-lookup"><span data-stu-id="eab5b-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eab5b-112">需求</span><span class="sxs-lookup"><span data-stu-id="eab5b-112">Requirements</span></span>  
 <span data-ttu-id="eab5b-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="eab5b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab5b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eab5b-114">See also</span></span>

- [<span data-ttu-id="eab5b-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="eab5b-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="eab5b-116">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="eab5b-116">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
