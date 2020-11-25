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
ms.openlocfilehash: 2136eb32f147b8928e6ac90b99bbdf66804f244d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733265"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="bc1f9-102">ISymUnmanagedWriter::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="bc1f9-102">ISymUnmanagedWriter::Abort Method</span></span>

<span data-ttu-id="bc1f9-103">關閉符號寫入器，而不將符號認可到符號存放區。</span><span class="sxs-lookup"><span data-stu-id="bc1f9-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="bc1f9-104">在這個呼叫之後，符號寫入器會變成無效，以供進一步的更新。</span><span class="sxs-lookup"><span data-stu-id="bc1f9-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="bc1f9-105">若要認可符號並關閉符號寫入器，請改用 [ISymUnmanagedWriter：： close](isymunmanagedwriter-close-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="bc1f9-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="bc1f9-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bc1f9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc1f9-107">Return Value</span></span>  

 <span data-ttu-id="bc1f9-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bc1f9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1f9-109">需求</span><span class="sxs-lookup"><span data-stu-id="bc1f9-109">Requirements</span></span>  

 <span data-ttu-id="bc1f9-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bc1f9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1f9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc1f9-111">See also</span></span>

- [<span data-ttu-id="bc1f9-112">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bc1f9-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
