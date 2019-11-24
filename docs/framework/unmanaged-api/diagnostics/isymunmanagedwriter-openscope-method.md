---
title: ISymUnmanagedWriter::OpenScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 915b05d0d2ac611678fdcc94dd42bbb1962e6ceb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427889"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="47d17-102">ISymUnmanagedWriter::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="47d17-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="47d17-103">開啟目前方法中的新語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="47d17-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="47d17-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span><span class="sxs-lookup"><span data-stu-id="47d17-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="47d17-105">Scopes must form a hierarchy.</span><span class="sxs-lookup"><span data-stu-id="47d17-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="47d17-106">Siblings are not allowed to overlap.</span><span class="sxs-lookup"><span data-stu-id="47d17-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d17-107">語法</span><span class="sxs-lookup"><span data-stu-id="47d17-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47d17-108">參數</span><span class="sxs-lookup"><span data-stu-id="47d17-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="47d17-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span><span class="sxs-lookup"><span data-stu-id="47d17-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="47d17-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span><span class="sxs-lookup"><span data-stu-id="47d17-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47d17-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="47d17-111">Return Value</span></span>  
 <span data-ttu-id="47d17-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="47d17-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47d17-113">備註</span><span class="sxs-lookup"><span data-stu-id="47d17-113">Remarks</span></span>  
 <span data-ttu-id="47d17-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span><span class="sxs-lookup"><span data-stu-id="47d17-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="47d17-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span><span class="sxs-lookup"><span data-stu-id="47d17-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="47d17-116">Scope identifiers are valid only in the current method.</span><span class="sxs-lookup"><span data-stu-id="47d17-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47d17-117">需求</span><span class="sxs-lookup"><span data-stu-id="47d17-117">Requirements</span></span>  
 <span data-ttu-id="47d17-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47d17-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d17-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="47d17-119">See also</span></span>

- [<span data-ttu-id="47d17-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="47d17-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
