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
ms.openlocfilehash: 90f5924bc03a9896442fd61a4c618d18ed999faf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638869"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="3d6c8-102">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="3d6c8-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="3d6c8-103">處置 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="3d6c8-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d6c8-104">方法</span><span class="sxs-lookup"><span data-stu-id="3d6c8-104">Methods</span></span>  
  
|<span data-ttu-id="3d6c8-105">方法</span><span class="sxs-lookup"><span data-stu-id="3d6c8-105">Method</span></span>|<span data-ttu-id="3d6c8-106">描述</span><span class="sxs-lookup"><span data-stu-id="3d6c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d6c8-107">Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="3d6c8-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="3d6c8-108">讓基礎的物件釋放所有的內部參考，並在任何後續的方法呼叫傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="3d6c8-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d6c8-109">需求</span><span class="sxs-lookup"><span data-stu-id="3d6c8-109">Requirements</span></span>  
 <span data-ttu-id="3d6c8-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3d6c8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6c8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d6c8-111">See also</span></span>
- [<span data-ttu-id="3d6c8-112">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="3d6c8-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
