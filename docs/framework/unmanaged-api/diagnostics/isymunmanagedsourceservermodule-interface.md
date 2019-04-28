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
ms.openlocfilehash: 3ba81c208c4b49342c6a055e09ba898871db1851
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922131"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="4e1f5-102">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="4e1f5-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="4e1f5-103">提供來源伺服器資料模組。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-103">Provides source server data for a module.</span></span> <span data-ttu-id="4e1f5-104">取得這個介面，藉由呼叫`QueryInterface`上實作的物件[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e1f5-105">方法</span><span class="sxs-lookup"><span data-stu-id="4e1f5-105">Methods</span></span>  
  
|<span data-ttu-id="4e1f5-106">方法</span><span class="sxs-lookup"><span data-stu-id="4e1f5-106">Method</span></span>|<span data-ttu-id="4e1f5-107">描述</span><span class="sxs-lookup"><span data-stu-id="4e1f5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e1f5-108">GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="4e1f5-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="4e1f5-109">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e1f5-110">需求</span><span class="sxs-lookup"><span data-stu-id="4e1f5-110">Requirements</span></span>  
 <span data-ttu-id="4e1f5-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4e1f5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e1f5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e1f5-112">See also</span></span>

- [<span data-ttu-id="4e1f5-113">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="4e1f5-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
