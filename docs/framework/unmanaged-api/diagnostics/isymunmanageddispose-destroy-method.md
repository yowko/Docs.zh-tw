---
title: "ISymUnmanagedDispose::Destroy 方法"
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
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d418bbb476fea306bf9ad92ce2b30d558627009
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="8d2fe-102">ISymUnmanagedDispose::Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="8d2fe-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="8d2fe-103">會造成基礎物件釋放所有的內部參考和任何後續方法呼叫傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="8d2fe-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d2fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d2fe-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8d2fe-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d2fe-105">Return Value</span></span>  
 <span data-ttu-id="8d2fe-106">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8d2fe-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d2fe-107">需求</span><span class="sxs-lookup"><span data-stu-id="8d2fe-107">Requirements</span></span>  
 <span data-ttu-id="8d2fe-108">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8d2fe-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2fe-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d2fe-109">See Also</span></span>  
 [<span data-ttu-id="8d2fe-110">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="8d2fe-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
