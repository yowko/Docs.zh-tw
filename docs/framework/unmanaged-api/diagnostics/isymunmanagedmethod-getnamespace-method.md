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
ms.openlocfilehash: b8bbedb4c60a2df6070373f2b6a104fff094869a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448975"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="2b09c-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="2b09c-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="2b09c-103">Gets the namespace within which this method is defined.</span><span class="sxs-lookup"><span data-stu-id="2b09c-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b09c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b09c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b09c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b09c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2b09c-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2b09c-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b09c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b09c-107">Return Value</span></span>  
 <span data-ttu-id="2b09c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="2b09c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b09c-109">需求</span><span class="sxs-lookup"><span data-stu-id="2b09c-109">Requirements</span></span>  
 <span data-ttu-id="2b09c-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2b09c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b09c-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b09c-111">See also</span></span>

- [<span data-ttu-id="2b09c-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="2b09c-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
