---
title: "ISymUnmanagedWriter::Close 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70f710802862c3237cbd67693f8366946926891e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="7a26a-102">ISymUnmanagedWriter::Close 方法</span><span class="sxs-lookup"><span data-stu-id="7a26a-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="7a26a-103">關閉後認可到符號存放區的符號的符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="7a26a-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a26a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a26a-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7a26a-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="7a26a-105">Return Value</span></span>  
 <span data-ttu-id="7a26a-106">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7a26a-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a26a-107">備註</span><span class="sxs-lookup"><span data-stu-id="7a26a-107">Remarks</span></span>  
 <span data-ttu-id="7a26a-108">呼叫後，符號寫入器會變成無效的進一步更新。</span><span class="sxs-lookup"><span data-stu-id="7a26a-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="7a26a-109">若要關閉符號寫入器未認可的符號，請使用[isymunmanagedwriter:: Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="7a26a-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a26a-110">需求</span><span class="sxs-lookup"><span data-stu-id="7a26a-110">Requirements</span></span>  
 <span data-ttu-id="7a26a-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a26a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a26a-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a26a-112">See Also</span></span>  
 [<span data-ttu-id="7a26a-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="7a26a-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
