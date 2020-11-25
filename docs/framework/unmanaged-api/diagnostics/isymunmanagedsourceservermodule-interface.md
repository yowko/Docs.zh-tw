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
ms.openlocfilehash: 5e438c75a29984e9200dc240f389f079a4eecfd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733950"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="51c02-102">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="51c02-102">ISymUnmanagedSourceServerModule Interface</span></span>

<span data-ttu-id="51c02-103">提供模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="51c02-103">Provides source server data for a module.</span></span> <span data-ttu-id="51c02-104">`QueryInterface`在實[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的物件上呼叫，以取得這個介面。</span><span class="sxs-lookup"><span data-stu-id="51c02-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51c02-105">方法</span><span class="sxs-lookup"><span data-stu-id="51c02-105">Methods</span></span>  
  
|<span data-ttu-id="51c02-106">方法</span><span class="sxs-lookup"><span data-stu-id="51c02-106">Method</span></span>|<span data-ttu-id="51c02-107">描述</span><span class="sxs-lookup"><span data-stu-id="51c02-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51c02-108">GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="51c02-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="51c02-109">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="51c02-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51c02-110">需求</span><span class="sxs-lookup"><span data-stu-id="51c02-110">Requirements</span></span>  

 <span data-ttu-id="51c02-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="51c02-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c02-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51c02-112">See also</span></span>

- [<span data-ttu-id="51c02-113">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="51c02-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
