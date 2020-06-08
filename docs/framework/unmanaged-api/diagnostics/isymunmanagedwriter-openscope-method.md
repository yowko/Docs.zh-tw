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
ms.openlocfilehash: 2808606be24399c9a4fe03df4c53202d31cbbe91
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501712"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="1ae65-102">ISymUnmanagedWriter::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="1ae65-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="1ae65-103">開啟目前方法中的新語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="1ae65-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="1ae65-104">範圍會變成新的目前範圍，並推送至範圍的堆疊。</span><span class="sxs-lookup"><span data-stu-id="1ae65-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="1ae65-105">範圍必須形成階層。</span><span class="sxs-lookup"><span data-stu-id="1ae65-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="1ae65-106">同級不允許重迭。</span><span class="sxs-lookup"><span data-stu-id="1ae65-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae65-107">語法</span><span class="sxs-lookup"><span data-stu-id="1ae65-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ae65-108">參數</span><span class="sxs-lookup"><span data-stu-id="1ae65-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="1ae65-109">在從方法開頭算起的詞法範圍中，第一個指令的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1ae65-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1ae65-110">脫銷`ULONG32`接收範圍識別碼之的指標。</span><span class="sxs-lookup"><span data-stu-id="1ae65-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ae65-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ae65-111">Return Value</span></span>  
 <span data-ttu-id="1ae65-112">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1ae65-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae65-113">備註</span><span class="sxs-lookup"><span data-stu-id="1ae65-113">Remarks</span></span>  
 <span data-ttu-id="1ae65-114">`ISymUnmanagedWriter::OpenScope`傳回不透明的範圍識別碼，可以與[ISymUnmanagedWriter：： SetScopeRange](isymunmanagedwriter-setscoperange-method.md)搭配使用，以便稍後定義範圍的開始和結束位移。</span><span class="sxs-lookup"><span data-stu-id="1ae65-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="1ae65-115">在此情況下，傳遞至 `ISymUnmanagedWriter::OpenScope` 和[ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md)的位移會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1ae65-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="1ae65-116">範圍識別碼只在目前的方法中有效。</span><span class="sxs-lookup"><span data-stu-id="1ae65-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae65-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="1ae65-117">Requirements</span></span>  
 <span data-ttu-id="1ae65-118">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="1ae65-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae65-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae65-119">See also</span></span>

- [<span data-ttu-id="1ae65-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="1ae65-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
