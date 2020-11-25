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
ms.openlocfilehash: 5afc91d1dc6d02f052e860787ebf0858a2f5d12d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730041"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="acf95-102">ISymUnmanagedWriter::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="acf95-102">ISymUnmanagedWriter::OpenScope Method</span></span>

<span data-ttu-id="acf95-103">開啟目前方法中的新語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="acf95-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="acf95-104">範圍會變成新的目前範圍，並推送至範圍的堆疊。</span><span class="sxs-lookup"><span data-stu-id="acf95-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="acf95-105">範圍必須形成階層。</span><span class="sxs-lookup"><span data-stu-id="acf95-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="acf95-106">不允許將同級重迭。</span><span class="sxs-lookup"><span data-stu-id="acf95-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf95-107">語法</span><span class="sxs-lookup"><span data-stu-id="acf95-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acf95-108">參數</span><span class="sxs-lookup"><span data-stu-id="acf95-108">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="acf95-109">在從方法的開頭開始，詞法範圍中第一個指令的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="acf95-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="acf95-110">擴展 `ULONG32` 接收範圍識別碼之的指標。</span><span class="sxs-lookup"><span data-stu-id="acf95-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acf95-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="acf95-111">Return Value</span></span>  

 <span data-ttu-id="acf95-112">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="acf95-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acf95-113">備註</span><span class="sxs-lookup"><span data-stu-id="acf95-113">Remarks</span></span>  

 <span data-ttu-id="acf95-114">`ISymUnmanagedWriter::OpenScope` 傳回不透明的範圍識別碼，這個識別碼可以與 [ISymUnmanagedWriter：： SetScopeRange](isymunmanagedwriter-setscoperange-method.md) 搭配使用，以定義稍後的範圍開始和結束位移。</span><span class="sxs-lookup"><span data-stu-id="acf95-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="acf95-115">在此情況下， `ISymUnmanagedWriter::OpenScope` 會忽略傳遞給和 [ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md) 的位移。</span><span class="sxs-lookup"><span data-stu-id="acf95-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="acf95-116">範圍識別碼只有在目前方法中才有效。</span><span class="sxs-lookup"><span data-stu-id="acf95-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf95-117">需求</span><span class="sxs-lookup"><span data-stu-id="acf95-117">Requirements</span></span>  

 <span data-ttu-id="acf95-118">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="acf95-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf95-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acf95-119">See also</span></span>

- [<span data-ttu-id="acf95-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="acf95-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
