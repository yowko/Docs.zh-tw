---
title: "ISymUnmanagedNamespace::GetNamespaces 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69ee0f6385abf78a368d488d0190796516c4f3d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="1614b-102">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="1614b-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="1614b-103">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="1614b-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1614b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1614b-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1614b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1614b-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="1614b-106">[in]A`ULONG32`指出的大小`namespaces`陣列。</span><span class="sxs-lookup"><span data-stu-id="1614b-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="1614b-107">[out]指標`ULONG32`接收以字元為單位，包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="1614b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="1614b-108">[out]包含命名空間緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1614b-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1614b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1614b-109">Return Value</span></span>  
 <span data-ttu-id="1614b-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1614b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1614b-111">需求</span><span class="sxs-lookup"><span data-stu-id="1614b-111">Requirements</span></span>  
 <span data-ttu-id="1614b-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1614b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1614b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="1614b-113">See Also</span></span>  
 [<span data-ttu-id="1614b-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="1614b-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
