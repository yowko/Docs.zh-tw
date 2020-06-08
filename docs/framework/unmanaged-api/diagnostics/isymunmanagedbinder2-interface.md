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
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501829"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="d2898-102">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="d2898-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="d2898-103">表示非受控程式碼的符號系結器，並擴充[ISymUnmanagedBinder](isymunmanagedbinder-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="d2898-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d2898-104">從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="d2898-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2898-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2898-105">Methods</span></span>  
  
|<span data-ttu-id="d2898-106">方法</span><span class="sxs-lookup"><span data-stu-id="d2898-106">Method</span></span>|<span data-ttu-id="d2898-107">描述</span><span class="sxs-lookup"><span data-stu-id="d2898-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2898-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="d2898-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="d2898-109">提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面，以便讀取與模組相關聯的偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="d2898-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="d2898-110">提供比[ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)方法更廣泛的搜尋。</span><span class="sxs-lookup"><span data-stu-id="d2898-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2898-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="d2898-111">Requirements</span></span>  
 <span data-ttu-id="d2898-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d2898-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2898-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2898-113">See also</span></span>

- [<span data-ttu-id="d2898-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d2898-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d2898-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="d2898-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="d2898-116">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="d2898-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
