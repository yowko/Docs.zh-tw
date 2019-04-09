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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105805"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="be3ea-102">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="be3ea-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="be3ea-103">表示 unmanaged 程式碼的符號繫結器。</span><span class="sxs-lookup"><span data-stu-id="be3ea-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be3ea-104">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="be3ea-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be3ea-105">方法</span><span class="sxs-lookup"><span data-stu-id="be3ea-105">Methods</span></span>  
  
|<span data-ttu-id="be3ea-106">方法</span><span class="sxs-lookup"><span data-stu-id="be3ea-106">Method</span></span>|<span data-ttu-id="be3ea-107">描述</span><span class="sxs-lookup"><span data-stu-id="be3ea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be3ea-108">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="be3ea-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="be3ea-109">提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的結構。</span><span class="sxs-lookup"><span data-stu-id="be3ea-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="be3ea-110">GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="be3ea-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="be3ea-111">提供中繼資料介面並包含符號存放區的資料流，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)指定的符號存放區的結構，將讀取偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="be3ea-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be3ea-112">需求</span><span class="sxs-lookup"><span data-stu-id="be3ea-112">Requirements</span></span>  
 <span data-ttu-id="be3ea-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="be3ea-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be3ea-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be3ea-114">See also</span></span>

- [<span data-ttu-id="be3ea-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="be3ea-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="be3ea-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="be3ea-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="be3ea-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="be3ea-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
