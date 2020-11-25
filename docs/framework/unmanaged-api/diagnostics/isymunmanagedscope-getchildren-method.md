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
ms.openlocfilehash: 8f3c83a7a89553ba600f3e0e368eec0ddd0350e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727604"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="9e3c4-102">ISymUnmanagedScope::GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="9e3c4-102">ISymUnmanagedScope::GetChildren Method</span></span>

<span data-ttu-id="9e3c4-103">取得此範圍的子系。</span><span class="sxs-lookup"><span data-stu-id="9e3c4-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e3c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e3c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e3c4-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e3c4-105">Parameters</span></span>  

 `cChildren`  
 <span data-ttu-id="9e3c4-106">在 `ULONG32` ，指出陣列的大小 `children` 。</span><span class="sxs-lookup"><span data-stu-id="9e3c4-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="9e3c4-107">擴展的指標 `ULONG32` ，會接收包含子系所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="9e3c4-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="9e3c4-108">擴展傳回的子係數組。</span><span class="sxs-lookup"><span data-stu-id="9e3c4-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e3c4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9e3c4-109">Return Value</span></span>  

 <span data-ttu-id="9e3c4-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9e3c4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e3c4-111">需求</span><span class="sxs-lookup"><span data-stu-id="9e3c4-111">Requirements</span></span>  

 <span data-ttu-id="9e3c4-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9e3c4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3c4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e3c4-113">See also</span></span>

- [<span data-ttu-id="9e3c4-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="9e3c4-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="9e3c4-115">GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="9e3c4-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
