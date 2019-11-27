---
title: ISymUnmanagedBinder 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: f23df98abc5355f0b25d7253b5f2ae808b3446a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449367"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="777fa-102">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="777fa-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="777fa-103">表示非受控程式碼的符號系結器。</span><span class="sxs-lookup"><span data-stu-id="777fa-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="777fa-104">從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="777fa-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="777fa-105">方法</span><span class="sxs-lookup"><span data-stu-id="777fa-105">Methods</span></span>  
  
|<span data-ttu-id="777fa-106">方法</span><span class="sxs-lookup"><span data-stu-id="777fa-106">Method</span></span>|<span data-ttu-id="777fa-107">描述</span><span class="sxs-lookup"><span data-stu-id="777fa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="777fa-108">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="777fa-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="777fa-109">提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)結構，以讀取與模組相關聯的偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="777fa-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="777fa-110">GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="777fa-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="777fa-111">假設中繼資料介面和包含符號存放區的資料流程，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)結構，以便從指定的符號存放區讀取偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="777fa-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="777fa-112">需求</span><span class="sxs-lookup"><span data-stu-id="777fa-112">Requirements</span></span>  
 <span data-ttu-id="777fa-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="777fa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777fa-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="777fa-114">See also</span></span>

- [<span data-ttu-id="777fa-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="777fa-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="777fa-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="777fa-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="777fa-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="777fa-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
