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
ms.openlocfilehash: a6f514cc070a0a38eb09a5387efc8611100765b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944101"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="0aedd-102">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="0aedd-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="0aedd-103">擴充符號系結器介面。</span><span class="sxs-lookup"><span data-stu-id="0aedd-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="0aedd-104">在執行`ISymUnmanagedBinder`介面的物件`QueryInterface`上呼叫, 以取得此介面。</span><span class="sxs-lookup"><span data-stu-id="0aedd-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0aedd-105">從不受信任的來源開啟程式資料庫 (PDB) 檔案會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="0aedd-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0aedd-106">方法</span><span class="sxs-lookup"><span data-stu-id="0aedd-106">Methods</span></span>  
  
|<span data-ttu-id="0aedd-107">方法</span><span class="sxs-lookup"><span data-stu-id="0aedd-107">Method</span></span>|<span data-ttu-id="0aedd-108">描述</span><span class="sxs-lookup"><span data-stu-id="0aedd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0aedd-109">GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="0aedd-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="0aedd-110">可讓使用者透過回呼`IID_IDiaReadExeAtRVACallback`來執行或提供, 或`IID_IDiaReadExeAtOffsetCallback`從記憶體取得 Debug 目錄資訊</span><span class="sxs-lookup"><span data-stu-id="0aedd-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0aedd-111">需求</span><span class="sxs-lookup"><span data-stu-id="0aedd-111">Requirements</span></span>  
 <span data-ttu-id="0aedd-112">**標頭：** CorSym .idl, CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0aedd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aedd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aedd-113">See also</span></span>

- [<span data-ttu-id="0aedd-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="0aedd-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0aedd-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="0aedd-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="0aedd-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="0aedd-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
