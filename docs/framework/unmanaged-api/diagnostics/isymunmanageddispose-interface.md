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
ms.openlocfilehash: 932e76e73d5d40b36abcb17d8a53e6745927d873
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719602"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="7f900-102">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="7f900-102">ISymUnmanagedDispose Interface</span></span>

<span data-ttu-id="7f900-103">處置未受管理的資源。</span><span class="sxs-lookup"><span data-stu-id="7f900-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f900-104">方法</span><span class="sxs-lookup"><span data-stu-id="7f900-104">Methods</span></span>  
  
|<span data-ttu-id="7f900-105">方法</span><span class="sxs-lookup"><span data-stu-id="7f900-105">Method</span></span>|<span data-ttu-id="7f900-106">描述</span><span class="sxs-lookup"><span data-stu-id="7f900-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f900-107">Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="7f900-107">Destroy Method</span></span>](isymunmanageddispose-destroy-method.md)|<span data-ttu-id="7f900-108">導致基礎物件釋放所有的內部參考，並在任何後續的方法呼叫上傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="7f900-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f900-109">需求</span><span class="sxs-lookup"><span data-stu-id="7f900-109">Requirements</span></span>  

 <span data-ttu-id="7f900-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="7f900-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f900-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f900-111">See also</span></span>

- [<span data-ttu-id="7f900-112">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="7f900-112">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
