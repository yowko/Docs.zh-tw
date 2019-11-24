---
title: ISymUnmanagedSourceServerModule 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: 9eac87d7627f502b13d805b8c5656e01ac578e7f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446203"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="db81e-102">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="db81e-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="db81e-103">Provides source server data for a module.</span><span class="sxs-lookup"><span data-stu-id="db81e-103">Provides source server data for a module.</span></span> <span data-ttu-id="db81e-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="db81e-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db81e-105">方法</span><span class="sxs-lookup"><span data-stu-id="db81e-105">Methods</span></span>  
  
|<span data-ttu-id="db81e-106">方法</span><span class="sxs-lookup"><span data-stu-id="db81e-106">Method</span></span>|<span data-ttu-id="db81e-107">描述</span><span class="sxs-lookup"><span data-stu-id="db81e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db81e-108">GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="db81e-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="db81e-109">Returns the source server data for the module.</span><span class="sxs-lookup"><span data-stu-id="db81e-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db81e-110">需求</span><span class="sxs-lookup"><span data-stu-id="db81e-110">Requirements</span></span>  
 <span data-ttu-id="db81e-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db81e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db81e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="db81e-112">See also</span></span>

- [<span data-ttu-id="db81e-113">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="db81e-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
