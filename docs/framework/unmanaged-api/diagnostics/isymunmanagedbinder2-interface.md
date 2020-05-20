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
ms.openlocfilehash: 8a4fbb40ec2426d000628fbd6d5f0241d3152c18
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441665"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="e2167-102">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="e2167-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="e2167-103">表示非受控程式碼的符號系結器，並擴充[ISymUnmanagedBinder](isymunmanagedbinder-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e2167-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2167-104">從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="e2167-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2167-105">方法</span><span class="sxs-lookup"><span data-stu-id="e2167-105">Methods</span></span>  
  
|<span data-ttu-id="e2167-106">方法</span><span class="sxs-lookup"><span data-stu-id="e2167-106">Method</span></span>|<span data-ttu-id="e2167-107">描述</span><span class="sxs-lookup"><span data-stu-id="e2167-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2167-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="e2167-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="e2167-109">提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面，以便讀取與模組相關聯的偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="e2167-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="e2167-110">提供比[ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)方法更廣泛的搜尋。</span><span class="sxs-lookup"><span data-stu-id="e2167-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2167-111">需求</span><span class="sxs-lookup"><span data-stu-id="e2167-111">Requirements</span></span>  
 <span data-ttu-id="e2167-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e2167-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2167-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2167-113">See also</span></span>

- [<span data-ttu-id="e2167-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="e2167-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e2167-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="e2167-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="e2167-116">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="e2167-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
