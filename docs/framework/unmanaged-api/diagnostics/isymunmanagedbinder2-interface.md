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
ms.openlocfilehash: 29501eeb6085dbc235112d98e8099fcfa4565000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427791"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="0100a-102">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="0100a-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="0100a-103">表示 unmanaged 程式碼的符號繫結器，並擴充[ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="0100a-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0100a-104">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="0100a-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0100a-105">方法</span><span class="sxs-lookup"><span data-stu-id="0100a-105">Methods</span></span>  
  
|<span data-ttu-id="0100a-106">方法</span><span class="sxs-lookup"><span data-stu-id="0100a-106">Method</span></span>|<span data-ttu-id="0100a-107">描述</span><span class="sxs-lookup"><span data-stu-id="0100a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0100a-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="0100a-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="0100a-109">提供中繼資料介面和檔案名稱，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="0100a-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="0100a-110">提供比更廣泛的搜尋[isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0100a-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0100a-111">需求</span><span class="sxs-lookup"><span data-stu-id="0100a-111">Requirements</span></span>  
 <span data-ttu-id="0100a-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0100a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0100a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0100a-113">See Also</span></span>  
 [<span data-ttu-id="0100a-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="0100a-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="0100a-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="0100a-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="0100a-116">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="0100a-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
