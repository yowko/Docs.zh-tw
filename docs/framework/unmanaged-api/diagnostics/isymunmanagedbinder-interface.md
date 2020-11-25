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
ms.openlocfilehash: 554e59484f00626726f7f024c69e93a5e6647130
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727376"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="45ee0-102">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="45ee0-102">ISymUnmanagedBinder Interface</span></span>

<span data-ttu-id="45ee0-103">代表非受控碼的符號繫結器。</span><span class="sxs-lookup"><span data-stu-id="45ee0-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45ee0-104">從不受信任的來源開啟程式資料庫 (PDB) 檔案，會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="45ee0-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45ee0-105">方法</span><span class="sxs-lookup"><span data-stu-id="45ee0-105">Methods</span></span>  
  
|<span data-ttu-id="45ee0-106">方法</span><span class="sxs-lookup"><span data-stu-id="45ee0-106">Method</span></span>|<span data-ttu-id="45ee0-107">描述</span><span class="sxs-lookup"><span data-stu-id="45ee0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45ee0-108">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="45ee0-108">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="45ee0-109">指定中繼資料介面和檔案名之後，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 結構，以讀取與模組相關聯的偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="45ee0-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="45ee0-110">GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="45ee0-110">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="45ee0-111">指定中繼資料介面和包含符號存放區的資料流程時，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 結構，以便從指定的符號存放區讀取偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="45ee0-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45ee0-112">需求</span><span class="sxs-lookup"><span data-stu-id="45ee0-112">Requirements</span></span>  

 <span data-ttu-id="45ee0-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="45ee0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ee0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45ee0-114">See also</span></span>

- [<span data-ttu-id="45ee0-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="45ee0-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="45ee0-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="45ee0-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="45ee0-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="45ee0-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
