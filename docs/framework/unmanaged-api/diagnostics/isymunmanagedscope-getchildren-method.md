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
ms.openlocfilehash: c7e9d2fe94c33127d8b105333ad6dac9d6cc5af6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446368"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="987eb-102">ISymUnmanagedScope::GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="987eb-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="987eb-103">取得此範圍的子系。</span><span class="sxs-lookup"><span data-stu-id="987eb-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="987eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="987eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="987eb-105">參數</span><span class="sxs-lookup"><span data-stu-id="987eb-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="987eb-106">在表示 `children` 陣列大小的 `ULONG32`。</span><span class="sxs-lookup"><span data-stu-id="987eb-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="987eb-107">脫銷`ULONG32` 的指標，接收包含子系所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="987eb-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="987eb-108">脫銷傳回的子係數組。</span><span class="sxs-lookup"><span data-stu-id="987eb-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="987eb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="987eb-109">Return Value</span></span>  
 <span data-ttu-id="987eb-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="987eb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="987eb-111">需求</span><span class="sxs-lookup"><span data-stu-id="987eb-111">Requirements</span></span>  
 <span data-ttu-id="987eb-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="987eb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987eb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="987eb-113">See also</span></span>

- [<span data-ttu-id="987eb-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="987eb-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="987eb-115">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="987eb-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
