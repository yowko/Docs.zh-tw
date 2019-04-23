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
ms.openlocfilehash: 3dc3c842bbb4b86b82d03848751673400bed193b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213034"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="d800e-102">ISymUnmanagedScope::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="d800e-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="d800e-103">取得此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d800e-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d800e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d800e-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d800e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d800e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="d800e-106">[in] `namespaces` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="d800e-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="d800e-107">[out]指標`ULONG32`接收包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="d800e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="d800e-108">[out]的陣列，接收的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d800e-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d800e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d800e-109">Return Value</span></span>  
 <span data-ttu-id="d800e-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d800e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d800e-111">需求</span><span class="sxs-lookup"><span data-stu-id="d800e-111">Requirements</span></span>  
 <span data-ttu-id="d800e-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d800e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d800e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d800e-113">See also</span></span>

- [<span data-ttu-id="d800e-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="d800e-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
