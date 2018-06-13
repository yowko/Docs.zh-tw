---
title: ISymUnmanagedDispose 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 973fc35bb99bea6b3302760763069b9df6c548e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424400"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="fb6c9-102">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="fb6c9-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="fb6c9-103">處置 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="fb6c9-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb6c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="fb6c9-104">Methods</span></span>  
  
|<span data-ttu-id="fb6c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="fb6c9-105">Method</span></span>|<span data-ttu-id="fb6c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="fb6c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb6c9-107">Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="fb6c9-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="fb6c9-108">會造成基礎物件釋放所有的內部參考和任何後續方法呼叫傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="fb6c9-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb6c9-109">需求</span><span class="sxs-lookup"><span data-stu-id="fb6c9-109">Requirements</span></span>  
 <span data-ttu-id="fb6c9-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb6c9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6c9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb6c9-111">See Also</span></span>  
 [<span data-ttu-id="fb6c9-112">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="fb6c9-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
