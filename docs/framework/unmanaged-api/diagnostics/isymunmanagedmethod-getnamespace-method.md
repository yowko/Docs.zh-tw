---
title: ISymUnmanagedMethod::GetNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2bba44af50607772f2a52203a47e21d8699f78b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716142"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="57877-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="57877-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="57877-103">取得這個方法會在其中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="57877-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57877-104">語法</span><span class="sxs-lookup"><span data-stu-id="57877-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57877-105">參數</span><span class="sxs-lookup"><span data-stu-id="57877-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="57877-106">[out]設定指標所傳回[ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="57877-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57877-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="57877-107">Return Value</span></span>  
 <span data-ttu-id="57877-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="57877-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57877-109">需求</span><span class="sxs-lookup"><span data-stu-id="57877-109">Requirements</span></span>  
 <span data-ttu-id="57877-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="57877-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57877-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57877-111">See also</span></span>
- [<span data-ttu-id="57877-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="57877-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
