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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2debe193b96b065987f6d7ebc6ffc1abac95778
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778207"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="fc7fb-102">ISymUnmanagedWriter::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="fc7fb-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="fc7fb-103">關閉的符號寫入器，而不需要認可至符號存放區的符號。</span><span class="sxs-lookup"><span data-stu-id="fc7fb-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="fc7fb-104">此呼叫之後，符號寫入器會變成無效的進一步更新。</span><span class="sxs-lookup"><span data-stu-id="fc7fb-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="fc7fb-105">若要認可的符號，並關閉的符號寫入器，請使用[isymunmanagedwriter:: Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="fc7fb-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc7fb-106">語法</span><span class="sxs-lookup"><span data-stu-id="fc7fb-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fc7fb-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc7fb-107">Return Value</span></span>  
 <span data-ttu-id="fc7fb-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fc7fb-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc7fb-109">需求</span><span class="sxs-lookup"><span data-stu-id="fc7fb-109">Requirements</span></span>  
 <span data-ttu-id="fc7fb-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc7fb-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7fb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc7fb-111">See also</span></span>

- [<span data-ttu-id="fc7fb-112">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="fc7fb-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
