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
ms.openlocfilehash: 6a31026f5b1669c0c29762048dc2c5c1c7bbb6a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732823"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="88dc8-102">ISymUnmanagedDispose::Destroy 方法</span><span class="sxs-lookup"><span data-stu-id="88dc8-102">ISymUnmanagedDispose::Destroy Method</span></span>

<span data-ttu-id="88dc8-103">導致基礎物件釋放所有的內部參考，並在任何後續的方法呼叫上傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="88dc8-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88dc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="88dc8-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="88dc8-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="88dc8-105">Return Value</span></span>  

 <span data-ttu-id="88dc8-106">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="88dc8-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88dc8-107">需求</span><span class="sxs-lookup"><span data-stu-id="88dc8-107">Requirements</span></span>  

 <span data-ttu-id="88dc8-108">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="88dc8-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dc8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88dc8-109">See also</span></span>

- [<span data-ttu-id="88dc8-110">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="88dc8-110">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
