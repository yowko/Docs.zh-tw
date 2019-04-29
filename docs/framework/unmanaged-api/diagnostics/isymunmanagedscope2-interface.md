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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0109b25b1cdc42204fc4873577e495641c4ec4fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761568"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="42464-102">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="42464-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="42464-103">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="42464-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="42464-104">這個介面會擴充[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面與方法，以取得關於常數所定義的範圍內。</span><span class="sxs-lookup"><span data-stu-id="42464-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42464-105">方法</span><span class="sxs-lookup"><span data-stu-id="42464-105">Methods</span></span>  
  
|<span data-ttu-id="42464-106">方法</span><span class="sxs-lookup"><span data-stu-id="42464-106">Method</span></span>|<span data-ttu-id="42464-107">描述</span><span class="sxs-lookup"><span data-stu-id="42464-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42464-108">GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="42464-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="42464-109">取得此範圍內所定義的計數。</span><span class="sxs-lookup"><span data-stu-id="42464-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="42464-110">GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="42464-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="42464-111">取得此範圍內定義的區域常數。</span><span class="sxs-lookup"><span data-stu-id="42464-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42464-112">需求</span><span class="sxs-lookup"><span data-stu-id="42464-112">Requirements</span></span>  
 <span data-ttu-id="42464-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="42464-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42464-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42464-114">See also</span></span>

- [<span data-ttu-id="42464-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="42464-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="42464-116">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="42464-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
