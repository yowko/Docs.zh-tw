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
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="42572-102">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="42572-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="42572-103">Represents a symbol binder for unmanaged code.</span><span class="sxs-lookup"><span data-stu-id="42572-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="42572-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span><span class="sxs-lookup"><span data-stu-id="42572-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42572-105">方法</span><span class="sxs-lookup"><span data-stu-id="42572-105">Methods</span></span>  
  
|<span data-ttu-id="42572-106">方法</span><span class="sxs-lookup"><span data-stu-id="42572-106">Method</span></span>|<span data-ttu-id="42572-107">描述</span><span class="sxs-lookup"><span data-stu-id="42572-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42572-108">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="42572-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="42572-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span><span class="sxs-lookup"><span data-stu-id="42572-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="42572-110">GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="42572-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="42572-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span><span class="sxs-lookup"><span data-stu-id="42572-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42572-112">需求</span><span class="sxs-lookup"><span data-stu-id="42572-112">Requirements</span></span>  
 <span data-ttu-id="42572-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="42572-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42572-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="42572-114">See also</span></span>

- [<span data-ttu-id="42572-115">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="42572-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="42572-116">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="42572-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="42572-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="42572-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
