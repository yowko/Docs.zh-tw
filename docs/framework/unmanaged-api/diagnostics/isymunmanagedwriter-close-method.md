---
title: ISymUnmanagedWriter::Close 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 1d684c14f14fcc93040798ae4ee3b8bb1df5354d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733252"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="e40c5-102">ISymUnmanagedWriter::Close 方法</span><span class="sxs-lookup"><span data-stu-id="e40c5-102">ISymUnmanagedWriter::Close Method</span></span>

<span data-ttu-id="e40c5-103">將符號認可到符號存放區之後，關閉符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="e40c5-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e40c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e40c5-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e40c5-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="e40c5-105">Return Value</span></span>  

 <span data-ttu-id="e40c5-106">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e40c5-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e40c5-107">備註</span><span class="sxs-lookup"><span data-stu-id="e40c5-107">Remarks</span></span>  

 <span data-ttu-id="e40c5-108">在這個呼叫之後，符號寫入器會變成無效，以供進一步的更新。</span><span class="sxs-lookup"><span data-stu-id="e40c5-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="e40c5-109">若要在不認可符號的情況下關閉符號寫入器，請改用 [ISymUnmanagedWriter：： Abort](isymunmanagedwriter-abort-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="e40c5-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e40c5-110">需求</span><span class="sxs-lookup"><span data-stu-id="e40c5-110">Requirements</span></span>  

 <span data-ttu-id="e40c5-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e40c5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40c5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e40c5-112">See also</span></span>

- [<span data-ttu-id="e40c5-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="e40c5-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
