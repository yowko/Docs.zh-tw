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
ms.openlocfilehash: 8300e3a7b324a2ff4acabeb30b30d2cdabc7c776
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449317"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="3a31a-102">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="3a31a-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="3a31a-103">表示非受控程式碼的符號系結器，並擴充[ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="3a31a-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a31a-104">從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="3a31a-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a31a-105">方法</span><span class="sxs-lookup"><span data-stu-id="3a31a-105">Methods</span></span>  
  
|<span data-ttu-id="3a31a-106">方法</span><span class="sxs-lookup"><span data-stu-id="3a31a-106">Method</span></span>|<span data-ttu-id="3a31a-107">描述</span><span class="sxs-lookup"><span data-stu-id="3a31a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a31a-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="3a31a-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="3a31a-109">提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面，以便讀取與模組相關聯的偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="3a31a-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="3a31a-110">提供比[ISymUnmanagedBinder：： GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法更廣泛的搜尋。</span><span class="sxs-lookup"><span data-stu-id="3a31a-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a31a-111">需求</span><span class="sxs-lookup"><span data-stu-id="3a31a-111">Requirements</span></span>  
 <span data-ttu-id="3a31a-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3a31a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a31a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a31a-113">See also</span></span>

- [<span data-ttu-id="3a31a-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="3a31a-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3a31a-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="3a31a-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="3a31a-116">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="3a31a-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
