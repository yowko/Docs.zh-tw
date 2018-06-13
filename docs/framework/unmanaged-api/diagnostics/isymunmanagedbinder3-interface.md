---
title: ISymUnmanagedBinder3 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06a4d5b1b108c15fa7ee4a7f5270b73f7adc1e6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426338"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="57521-102">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="57521-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="57521-103">擴充的符號繫結器介面。</span><span class="sxs-lookup"><span data-stu-id="57521-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="57521-104">取得此介面，藉由呼叫`QueryInterface`實作的物件上`ISymUnmanagedBinder`介面。</span><span class="sxs-lookup"><span data-stu-id="57521-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57521-105">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="57521-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57521-106">方法</span><span class="sxs-lookup"><span data-stu-id="57521-106">Methods</span></span>  
  
|<span data-ttu-id="57521-107">方法</span><span class="sxs-lookup"><span data-stu-id="57521-107">Method</span></span>|<span data-ttu-id="57521-108">描述</span><span class="sxs-lookup"><span data-stu-id="57521-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57521-109">GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="57521-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="57521-110">可讓使用者實作，或可能是提供透過回呼`IID_IDiaReadExeAtRVACallback`或`IID_IDiaReadExeAtOffsetCallback`取得偵錯資訊從記憶體</span><span class="sxs-lookup"><span data-stu-id="57521-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57521-111">需求</span><span class="sxs-lookup"><span data-stu-id="57521-111">Requirements</span></span>  
 <span data-ttu-id="57521-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="57521-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57521-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57521-113">See Also</span></span>  
 [<span data-ttu-id="57521-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="57521-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="57521-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="57521-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="57521-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="57521-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
