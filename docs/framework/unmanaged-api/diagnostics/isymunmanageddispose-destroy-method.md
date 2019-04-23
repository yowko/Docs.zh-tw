---
title: ISymUnmanagedDispose::Destroy 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51d2f0aedffdd88974a8184954ecbb9a231b70c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213665"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="604e3-102">ISymUnmanagedDispose::Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="604e3-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="604e3-103">讓基礎的物件釋放所有的內部參考，並在任何後續的方法呼叫傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="604e3-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="604e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="604e3-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="604e3-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="604e3-105">Return Value</span></span>  
 <span data-ttu-id="604e3-106">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="604e3-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="604e3-107">需求</span><span class="sxs-lookup"><span data-stu-id="604e3-107">Requirements</span></span>  
 <span data-ttu-id="604e3-108">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="604e3-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604e3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="604e3-109">See also</span></span>

- [<span data-ttu-id="604e3-110">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="604e3-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
