---
title: "ISymUnmanagedSourceServerModule 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f183c3ea69de15387f729a67328bf5ea57931750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="b91d3-102">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="b91d3-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="b91d3-103">提供模組中的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="b91d3-103">Provides source server data for a module.</span></span> <span data-ttu-id="b91d3-104">取得此介面，藉由呼叫`QueryInterface`實作的物件上[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b91d3-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b91d3-105">方法</span><span class="sxs-lookup"><span data-stu-id="b91d3-105">Methods</span></span>  
  
|<span data-ttu-id="b91d3-106">方法</span><span class="sxs-lookup"><span data-stu-id="b91d3-106">Method</span></span>|<span data-ttu-id="b91d3-107">描述</span><span class="sxs-lookup"><span data-stu-id="b91d3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b91d3-108">GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="b91d3-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="b91d3-109">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="b91d3-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b91d3-110">需求</span><span class="sxs-lookup"><span data-stu-id="b91d3-110">Requirements</span></span>  
 <span data-ttu-id="b91d3-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b91d3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91d3-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="b91d3-112">See Also</span></span>  
 [<span data-ttu-id="b91d3-113">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="b91d3-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
