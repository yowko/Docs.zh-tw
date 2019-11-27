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
ms.openlocfilehash: 08d9ba8f8c9a251bd0db0ffe256af7db0164ba2f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449223"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="3882a-102">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="3882a-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="3882a-103">處置非受控資源。</span><span class="sxs-lookup"><span data-stu-id="3882a-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3882a-104">方法</span><span class="sxs-lookup"><span data-stu-id="3882a-104">Methods</span></span>  
  
|<span data-ttu-id="3882a-105">方法</span><span class="sxs-lookup"><span data-stu-id="3882a-105">Method</span></span>|<span data-ttu-id="3882a-106">描述</span><span class="sxs-lookup"><span data-stu-id="3882a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3882a-107">Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="3882a-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="3882a-108">導致基礎物件釋放所有內部參考，並在任何後續的方法呼叫時傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="3882a-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3882a-109">需求</span><span class="sxs-lookup"><span data-stu-id="3882a-109">Requirements</span></span>  
 <span data-ttu-id="3882a-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3882a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3882a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3882a-111">See also</span></span>

- [<span data-ttu-id="3882a-112">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="3882a-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
