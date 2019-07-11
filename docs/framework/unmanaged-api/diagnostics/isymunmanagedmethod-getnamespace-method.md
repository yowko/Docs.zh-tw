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
ms.openlocfilehash: 676c968bb48e493f9a4514235fbc3246cf395228
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774656"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="205d0-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="205d0-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="205d0-103">取得這個方法會在其中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="205d0-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="205d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="205d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="205d0-105">參數</span><span class="sxs-lookup"><span data-stu-id="205d0-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="205d0-106">[out]設定指標所傳回[ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="205d0-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="205d0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="205d0-107">Return Value</span></span>  
 <span data-ttu-id="205d0-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="205d0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="205d0-109">需求</span><span class="sxs-lookup"><span data-stu-id="205d0-109">Requirements</span></span>  
 <span data-ttu-id="205d0-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="205d0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205d0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="205d0-111">See also</span></span>

- [<span data-ttu-id="205d0-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="205d0-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
