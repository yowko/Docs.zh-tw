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
ms.openlocfilehash: 0cb0b91f2dca8203c37599400b3b61f84eb7d282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727311"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="02f43-102">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="02f43-102">ISymUnmanagedBinder3 Interface</span></span>

<span data-ttu-id="02f43-103">擴充符號系結器介面。</span><span class="sxs-lookup"><span data-stu-id="02f43-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="02f43-104">藉由 `QueryInterface` 在執行介面的物件上呼叫來取得這個介面 `ISymUnmanagedBinder` 。</span><span class="sxs-lookup"><span data-stu-id="02f43-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="02f43-105">從不受信任的來源開啟程式資料庫 (PDB) 檔案，會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="02f43-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02f43-106">方法</span><span class="sxs-lookup"><span data-stu-id="02f43-106">Methods</span></span>  
  
|<span data-ttu-id="02f43-107">方法</span><span class="sxs-lookup"><span data-stu-id="02f43-107">Method</span></span>|<span data-ttu-id="02f43-108">描述</span><span class="sxs-lookup"><span data-stu-id="02f43-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02f43-109">GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="02f43-109">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="02f43-110">允許使用者透過回呼或 `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` 從記憶體中取得 Debug 目錄資訊來執行或提供</span><span class="sxs-lookup"><span data-stu-id="02f43-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02f43-111">需求</span><span class="sxs-lookup"><span data-stu-id="02f43-111">Requirements</span></span>  

 <span data-ttu-id="02f43-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="02f43-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f43-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f43-113">See also</span></span>

- [<span data-ttu-id="02f43-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="02f43-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="02f43-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="02f43-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="02f43-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="02f43-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
