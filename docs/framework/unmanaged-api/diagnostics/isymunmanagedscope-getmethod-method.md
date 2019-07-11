---
title: ISymUnmanagedScope::GetMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a75fed5e3272b783a6f8fb1a4f1c02096858b409
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777906"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="8069d-102">ISymUnmanagedScope::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="8069d-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="8069d-103">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="8069d-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8069d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8069d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8069d-105">參數</span><span class="sxs-lookup"><span data-stu-id="8069d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8069d-106">[out]所傳回的指標[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="8069d-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8069d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8069d-107">Return Value</span></span>  
 <span data-ttu-id="8069d-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8069d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8069d-109">需求</span><span class="sxs-lookup"><span data-stu-id="8069d-109">Requirements</span></span>  
 <span data-ttu-id="8069d-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8069d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8069d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8069d-111">See also</span></span>

- [<span data-ttu-id="8069d-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="8069d-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
