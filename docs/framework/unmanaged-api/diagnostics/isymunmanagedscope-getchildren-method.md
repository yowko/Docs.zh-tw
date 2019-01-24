---
title: ISymUnmanagedScope::GetChildren 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f9bd6ae34903798a29f8666dfdba3e102fae28db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584554"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="8ebc0-102">ISymUnmanagedScope::GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="8ebc0-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="8ebc0-103">取得此領域的子系。</span><span class="sxs-lookup"><span data-stu-id="8ebc0-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ebc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ebc0-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ebc0-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ebc0-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="8ebc0-106">[in]A`ULONG32`表示的大小`children`陣列。</span><span class="sxs-lookup"><span data-stu-id="8ebc0-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="8ebc0-107">[out]指標`ULONG32`接收包含子系所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="8ebc0-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="8ebc0-108">[out]子系傳回的陣列。</span><span class="sxs-lookup"><span data-stu-id="8ebc0-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ebc0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8ebc0-109">Return Value</span></span>  
 <span data-ttu-id="8ebc0-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ebc0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ebc0-111">需求</span><span class="sxs-lookup"><span data-stu-id="8ebc0-111">Requirements</span></span>  
 <span data-ttu-id="8ebc0-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ebc0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ebc0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ebc0-113">See also</span></span>
- [<span data-ttu-id="8ebc0-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="8ebc0-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="8ebc0-115">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="8ebc0-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
