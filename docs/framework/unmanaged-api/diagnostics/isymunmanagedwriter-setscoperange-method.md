---
title: ISymUnmanagedWriter::SetScopeRange 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d7fe8f36c7a5dbe6e715402fd7253092b64e68e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650748"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="a87e8-102">ISymUnmanagedWriter::SetScopeRange 方法</span><span class="sxs-lookup"><span data-stu-id="a87e8-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="a87e8-103">定義指定語彙範圍的位移範圍。</span><span class="sxs-lookup"><span data-stu-id="a87e8-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="a87e8-104">範圍會成為新的目前範圍，並推送至堆疊的範圍。</span><span class="sxs-lookup"><span data-stu-id="a87e8-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="a87e8-105">範圍必須形成階層。</span><span class="sxs-lookup"><span data-stu-id="a87e8-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="a87e8-106">同層級項目不允許重疊。</span><span class="sxs-lookup"><span data-stu-id="a87e8-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87e8-107">語法</span><span class="sxs-lookup"><span data-stu-id="a87e8-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a87e8-108">參數</span><span class="sxs-lookup"><span data-stu-id="a87e8-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="a87e8-109">[in]範圍的範圍識別項。</span><span class="sxs-lookup"><span data-stu-id="a87e8-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="a87e8-110">[in]位移，以位元組為單位，從一開始語彙範圍中的第一個指令的方法。</span><span class="sxs-lookup"><span data-stu-id="a87e8-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="a87e8-111">[in]位移，以位元組為單位，從一開始語彙範圍中的最後一個指令的方法。</span><span class="sxs-lookup"><span data-stu-id="a87e8-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a87e8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a87e8-112">Return Value</span></span>  
 <span data-ttu-id="a87e8-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a87e8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87e8-114">備註</span><span class="sxs-lookup"><span data-stu-id="a87e8-114">Remarks</span></span>  
 <span data-ttu-id="a87e8-115">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)傳回的不透明範圍識別項可以搭配使用`ISymUnmanagedWriter::SetScopeRange`定義範圍的開始和結束時間較晚的位移。</span><span class="sxs-lookup"><span data-stu-id="a87e8-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="a87e8-116">在此情況下，位移傳遞給`ISymUnmanagedWriter::OpenScope`並[isymunmanagedwriter:: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a87e8-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="a87e8-117">範圍識別項的有效期僅在目前的方法。</span><span class="sxs-lookup"><span data-stu-id="a87e8-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a87e8-118">需求</span><span class="sxs-lookup"><span data-stu-id="a87e8-118">Requirements</span></span>  
 <span data-ttu-id="a87e8-119">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a87e8-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87e8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87e8-120">See also</span></span>

- [<span data-ttu-id="a87e8-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a87e8-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
