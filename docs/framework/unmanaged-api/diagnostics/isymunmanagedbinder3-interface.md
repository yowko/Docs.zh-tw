---
title: "ISymUnmanagedBinder3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c93275fc32e68f49618d93bdd0b54f1970121ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="5e200-102">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="5e200-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="5e200-103">擴充的符號繫結器介面。</span><span class="sxs-lookup"><span data-stu-id="5e200-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="5e200-104">取得此介面，藉由呼叫`QueryInterface`實作的物件上`ISymUnmanagedBinder`介面。</span><span class="sxs-lookup"><span data-stu-id="5e200-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e200-105">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="5e200-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e200-106">方法</span><span class="sxs-lookup"><span data-stu-id="5e200-106">Methods</span></span>  
  
|<span data-ttu-id="5e200-107">方法</span><span class="sxs-lookup"><span data-stu-id="5e200-107">Method</span></span>|<span data-ttu-id="5e200-108">描述</span><span class="sxs-lookup"><span data-stu-id="5e200-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e200-109">GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="5e200-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="5e200-110">可讓使用者實作，或可能是提供透過回呼`IID_IDiaReadExeAtRVACallback`或`IID_IDiaReadExeAtOffsetCallback`取得偵錯資訊從記憶體</span><span class="sxs-lookup"><span data-stu-id="5e200-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e200-111">需求</span><span class="sxs-lookup"><span data-stu-id="5e200-111">Requirements</span></span>  
 <span data-ttu-id="5e200-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e200-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e200-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e200-113">See Also</span></span>  
 [<span data-ttu-id="5e200-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="5e200-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="5e200-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="5e200-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="5e200-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="5e200-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
