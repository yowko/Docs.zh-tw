---
title: "ISymUnmanagedWriter::Abort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Abort
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29dd11972e8db80f36820bba1eb679070d02146e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="94a89-102">ISymUnmanagedWriter::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="94a89-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="94a89-103">關閉不符號認可到符號存放區的符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="94a89-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="94a89-104">呼叫後，符號寫入器會變成無效的進一步更新。</span><span class="sxs-lookup"><span data-stu-id="94a89-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="94a89-105">若要認可符號，並關閉符號寫入器，請使用[isymunmanagedwriter:: Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="94a89-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a89-106">語法</span><span class="sxs-lookup"><span data-stu-id="94a89-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="94a89-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="94a89-107">Return Value</span></span>  
 <span data-ttu-id="94a89-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="94a89-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94a89-109">需求</span><span class="sxs-lookup"><span data-stu-id="94a89-109">Requirements</span></span>  
 <span data-ttu-id="94a89-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94a89-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a89-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a89-111">See Also</span></span>  
 [<span data-ttu-id="94a89-112">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="94a89-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
