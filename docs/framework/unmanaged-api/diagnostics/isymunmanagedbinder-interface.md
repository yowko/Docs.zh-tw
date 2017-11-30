---
title: "ISymUnmanagedBinder 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="cc998-102">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="cc998-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="cc998-103">表示 unmanaged 程式碼的符號繫結器。</span><span class="sxs-lookup"><span data-stu-id="cc998-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc998-104">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="cc998-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc998-105">方法</span><span class="sxs-lookup"><span data-stu-id="cc998-105">Methods</span></span>  
  
|<span data-ttu-id="cc998-106">方法</span><span class="sxs-lookup"><span data-stu-id="cc998-106">Method</span></span>|<span data-ttu-id="cc998-107">說明</span><span class="sxs-lookup"><span data-stu-id="cc998-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc998-108">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="cc998-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="cc998-109">提供中繼資料介面和檔案名稱，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 會讀取偵錯符號的模組相關聯的結構。</span><span class="sxs-lookup"><span data-stu-id="cc998-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="cc998-110">GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="cc998-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="cc998-111">提供中繼資料介面和包含符號存放區的資料流，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 從指定的符號存放區的結構，將讀取的偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="cc998-111">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc998-112">需求</span><span class="sxs-lookup"><span data-stu-id="cc998-112">Requirements</span></span>  
 <span data-ttu-id="cc998-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc998-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc998-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc998-114">See Also</span></span>  
 [<span data-ttu-id="cc998-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="cc998-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="cc998-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="cc998-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="cc998-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="cc998-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
