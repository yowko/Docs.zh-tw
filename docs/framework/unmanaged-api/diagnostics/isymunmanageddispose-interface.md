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
ms.openlocfilehash: 8e81cea13fb8d25701ccbe163f112904baf47a9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143158"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="27f58-102">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="27f58-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="27f58-103">處置 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="27f58-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27f58-104">方法</span><span class="sxs-lookup"><span data-stu-id="27f58-104">Methods</span></span>  
  
|<span data-ttu-id="27f58-105">方法</span><span class="sxs-lookup"><span data-stu-id="27f58-105">Method</span></span>|<span data-ttu-id="27f58-106">描述</span><span class="sxs-lookup"><span data-stu-id="27f58-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27f58-107">Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="27f58-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="27f58-108">讓基礎的物件釋放所有的內部參考，並在任何後續的方法呼叫傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="27f58-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27f58-109">需求</span><span class="sxs-lookup"><span data-stu-id="27f58-109">Requirements</span></span>  
 <span data-ttu-id="27f58-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27f58-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f58-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27f58-111">See also</span></span>

- [<span data-ttu-id="27f58-112">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="27f58-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
