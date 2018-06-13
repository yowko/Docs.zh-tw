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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a63700abf77d56134ca30620033c398af735599
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426735"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="78bf2-102">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="78bf2-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="78bf2-103">提供模組中的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="78bf2-103">Provides source server data for a module.</span></span> <span data-ttu-id="78bf2-104">取得此介面，藉由呼叫`QueryInterface`實作的物件上[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="78bf2-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78bf2-105">方法</span><span class="sxs-lookup"><span data-stu-id="78bf2-105">Methods</span></span>  
  
|<span data-ttu-id="78bf2-106">方法</span><span class="sxs-lookup"><span data-stu-id="78bf2-106">Method</span></span>|<span data-ttu-id="78bf2-107">描述</span><span class="sxs-lookup"><span data-stu-id="78bf2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78bf2-108">GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="78bf2-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="78bf2-109">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="78bf2-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78bf2-110">需求</span><span class="sxs-lookup"><span data-stu-id="78bf2-110">Requirements</span></span>  
 <span data-ttu-id="78bf2-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="78bf2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bf2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78bf2-112">See Also</span></span>  
 [<span data-ttu-id="78bf2-113">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="78bf2-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
