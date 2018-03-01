---
title: "ISymUnmanagedBinder 介面"
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
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79d3758f57976d08d4599de500e2e12e4d67cb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="7c8c6-102">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="7c8c6-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="7c8c6-103">表示 unmanaged 程式碼的符號繫結器。</span><span class="sxs-lookup"><span data-stu-id="7c8c6-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c8c6-104">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="7c8c6-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c8c6-105">方法</span><span class="sxs-lookup"><span data-stu-id="7c8c6-105">Methods</span></span>  
  
|<span data-ttu-id="7c8c6-106">方法</span><span class="sxs-lookup"><span data-stu-id="7c8c6-106">Method</span></span>|<span data-ttu-id="7c8c6-107">描述</span><span class="sxs-lookup"><span data-stu-id="7c8c6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c8c6-108">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="7c8c6-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="7c8c6-109">提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的結構。</span><span class="sxs-lookup"><span data-stu-id="7c8c6-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="7c8c6-110">GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="7c8c6-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="7c8c6-111">提供中繼資料介面和包含符號存放區的資料流，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)從給定的符號存放區的結構，將讀取的偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="7c8c6-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c8c6-112">需求</span><span class="sxs-lookup"><span data-stu-id="7c8c6-112">Requirements</span></span>  
 <span data-ttu-id="7c8c6-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7c8c6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8c6-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c8c6-114">See Also</span></span>  
 [<span data-ttu-id="7c8c6-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="7c8c6-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="7c8c6-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="7c8c6-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="7c8c6-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="7c8c6-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
