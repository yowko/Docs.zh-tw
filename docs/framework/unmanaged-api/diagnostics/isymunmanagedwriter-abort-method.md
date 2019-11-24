---
title: ISymUnmanagedWriter::Abort 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 6074ec5248d27b1405d2367349904f6630df951b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445990"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="5ebf9-102">ISymUnmanagedWriter::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="5ebf9-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="5ebf9-103">Closes the symbol writer without committing the symbols to the symbol store.</span><span class="sxs-lookup"><span data-stu-id="5ebf9-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="5ebf9-104">After this call, the symbol writer becomes invalid for further updates.</span><span class="sxs-lookup"><span data-stu-id="5ebf9-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="5ebf9-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span><span class="sxs-lookup"><span data-stu-id="5ebf9-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ebf9-106">語法</span><span class="sxs-lookup"><span data-stu-id="5ebf9-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5ebf9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5ebf9-107">Return Value</span></span>  
 <span data-ttu-id="5ebf9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="5ebf9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ebf9-109">需求</span><span class="sxs-lookup"><span data-stu-id="5ebf9-109">Requirements</span></span>  
 <span data-ttu-id="5ebf9-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5ebf9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebf9-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="5ebf9-111">See also</span></span>

- [<span data-ttu-id="5ebf9-112">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="5ebf9-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
