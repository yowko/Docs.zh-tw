---
title: ISymUnmanagedScope::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2c64d7ead2f7ce3d76b40f4fdc604506ee85561
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777887"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="5fa5d-102">ISymUnmanagedScope::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="5fa5d-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="5fa5d-103">取得此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5fa5d-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fa5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fa5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fa5d-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="5fa5d-106">[in] `namespaces` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="5fa5d-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="5fa5d-107">[out]指標`ULONG32`接收包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="5fa5d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="5fa5d-108">[out]的陣列，接收的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5fa5d-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fa5d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5fa5d-109">Return Value</span></span>  
 <span data-ttu-id="5fa5d-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5fa5d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fa5d-111">需求</span><span class="sxs-lookup"><span data-stu-id="5fa5d-111">Requirements</span></span>  
 <span data-ttu-id="5fa5d-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5fa5d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa5d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fa5d-113">See also</span></span>

- [<span data-ttu-id="5fa5d-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="5fa5d-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
