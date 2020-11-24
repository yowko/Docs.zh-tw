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
ms.openlocfilehash: 06dff4847ec3d15f446f1c89219b10eddb8eec4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683520"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="dd2ba-102">ISymUnmanagedWriter::SetScopeRange 方法</span><span class="sxs-lookup"><span data-stu-id="dd2ba-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>

<span data-ttu-id="dd2ba-103">定義指定語彙範圍的位移範圍。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="dd2ba-104">範圍會變成新的目前範圍，並推送至範圍的堆疊。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="dd2ba-105">範圍必須形成階層。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="dd2ba-106">不允許將同級重迭。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd2ba-107">語法</span><span class="sxs-lookup"><span data-stu-id="dd2ba-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd2ba-108">參數</span><span class="sxs-lookup"><span data-stu-id="dd2ba-108">Parameters</span></span>  

 `scopeId`  
 <span data-ttu-id="dd2ba-109">在範圍的範圍識別碼。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="dd2ba-110">在從方法開頭之詞法範圍中第一個指令的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="dd2ba-111">在從方法的開頭之詞法範圍中，最後一個指令的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd2ba-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="dd2ba-112">Return Value</span></span>  

 <span data-ttu-id="dd2ba-113">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd2ba-114">備註</span><span class="sxs-lookup"><span data-stu-id="dd2ba-114">Remarks</span></span>  

 <span data-ttu-id="dd2ba-115">[ISymUnmanagedWriter：： OpenScope](isymunmanagedwriter-openscope-method.md) 會傳回不透明的範圍識別碼，這個識別碼可以搭配使用 `ISymUnmanagedWriter::SetScopeRange` ，以定義稍後的範圍開始和結束位移。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-115">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="dd2ba-116">在此情況下， `ISymUnmanagedWriter::OpenScope` 會忽略傳遞給和 [ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md) 的位移。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="dd2ba-117">範圍識別碼只有在目前方法中才有效。</span><span class="sxs-lookup"><span data-stu-id="dd2ba-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd2ba-118">需求</span><span class="sxs-lookup"><span data-stu-id="dd2ba-118">Requirements</span></span>  

 <span data-ttu-id="dd2ba-119">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="dd2ba-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd2ba-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd2ba-120">See also</span></span>

- [<span data-ttu-id="dd2ba-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="dd2ba-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
