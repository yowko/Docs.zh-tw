---
title: ISymUnmanagedNamespace::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e11886917964134a2530ae8484dba3cde5e7b61
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759381"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="ae2f0-102">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="ae2f0-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="ae2f0-103">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="ae2f0-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae2f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae2f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae2f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae2f0-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="ae2f0-106">[in]A`ULONG32`表示的大小`namespaces`陣列。</span><span class="sxs-lookup"><span data-stu-id="ae2f0-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="ae2f0-107">[out]指標`ULONG32`接收大小，以字元為單位，以包含命名空間所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ae2f0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="ae2f0-108">[out]包含命名空間緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="ae2f0-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae2f0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae2f0-109">Return Value</span></span>  
 <span data-ttu-id="ae2f0-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2f0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae2f0-111">需求</span><span class="sxs-lookup"><span data-stu-id="ae2f0-111">Requirements</span></span>  
 <span data-ttu-id="ae2f0-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ae2f0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2f0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae2f0-113">See also</span></span>

- [<span data-ttu-id="ae2f0-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="ae2f0-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
