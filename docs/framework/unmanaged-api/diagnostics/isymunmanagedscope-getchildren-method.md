---
title: "ISymUnmanagedScope::GetChildren 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetChildren
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a43a0f46532bfb0eeaa4e385946a5aaa1b50eba8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="800a6-102">ISymUnmanagedScope::GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="800a6-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="800a6-103">取得此領域的子系。</span><span class="sxs-lookup"><span data-stu-id="800a6-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="800a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="800a6-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="800a6-105">參數</span><span class="sxs-lookup"><span data-stu-id="800a6-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="800a6-106">[in]A`ULONG32`指出的大小`children`陣列。</span><span class="sxs-lookup"><span data-stu-id="800a6-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="800a6-107">[out]指標`ULONG32`包含子系所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="800a6-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="800a6-108">[out]子系傳回的陣列。</span><span class="sxs-lookup"><span data-stu-id="800a6-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="800a6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="800a6-109">Return Value</span></span>  
 <span data-ttu-id="800a6-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="800a6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="800a6-111">需求</span><span class="sxs-lookup"><span data-stu-id="800a6-111">Requirements</span></span>  
 <span data-ttu-id="800a6-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="800a6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800a6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="800a6-113">See Also</span></span>  
 [<span data-ttu-id="800a6-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="800a6-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="800a6-115">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="800a6-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
