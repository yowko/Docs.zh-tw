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
ms.openlocfilehash: d90a55b53ba00540137e44fc190790c4710903e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610791"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="4e2f4-102">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="4e2f4-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="4e2f4-103">提供模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="4e2f4-103">Provides source server data for a module.</span></span> <span data-ttu-id="4e2f4-104">`QueryInterface`在執行[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得此介面。</span><span class="sxs-lookup"><span data-stu-id="4e2f4-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e2f4-105">方法</span><span class="sxs-lookup"><span data-stu-id="4e2f4-105">Methods</span></span>  
  
|<span data-ttu-id="4e2f4-106">方法</span><span class="sxs-lookup"><span data-stu-id="4e2f4-106">Method</span></span>|<span data-ttu-id="4e2f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="4e2f4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e2f4-108">GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="4e2f4-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="4e2f4-109">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="4e2f4-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e2f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="4e2f4-110">Requirements</span></span>  
 <span data-ttu-id="4e2f4-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="4e2f4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e2f4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e2f4-112">See also</span></span>

- [<span data-ttu-id="4e2f4-113">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="4e2f4-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
