---
title: ISymUnmanagedBinder2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52b0f6b9d3e0ea3d6fe5f14badb8401b1a0c2c63
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187488"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="db5e7-102">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="db5e7-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="db5e7-103">表示 unmanaged 程式碼的符號繫結器，並延伸[ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="db5e7-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db5e7-104">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="db5e7-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db5e7-105">方法</span><span class="sxs-lookup"><span data-stu-id="db5e7-105">Methods</span></span>  
  
|<span data-ttu-id="db5e7-106">方法</span><span class="sxs-lookup"><span data-stu-id="db5e7-106">Method</span></span>|<span data-ttu-id="db5e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="db5e7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db5e7-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="db5e7-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="db5e7-109">提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="db5e7-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="db5e7-110">提供更廣泛搜尋條件來得[isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="db5e7-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db5e7-111">需求</span><span class="sxs-lookup"><span data-stu-id="db5e7-111">Requirements</span></span>  
 <span data-ttu-id="db5e7-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db5e7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5e7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5e7-113">See Also</span></span>  
 [<span data-ttu-id="db5e7-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="db5e7-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="db5e7-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="db5e7-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="db5e7-116">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="db5e7-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
