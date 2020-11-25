---
title: ISymUnmanagedWriter::CloseScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: 561a6348b9976789b02961fadb37d9127f5a6a13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713037"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="6f551-102">ISymUnmanagedWriter::CloseScope 方法</span><span class="sxs-lookup"><span data-stu-id="6f551-102">ISymUnmanagedWriter::CloseScope Method</span></span>

<span data-ttu-id="6f551-103">關閉目前的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="6f551-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f551-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f551-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f551-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f551-105">Parameters</span></span>  

 `endOffset`  
 <span data-ttu-id="6f551-106">在從詞法範圍中最後一個指令結尾的點方法開頭的位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6f551-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f551-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f551-107">Return Value</span></span>  

 <span data-ttu-id="6f551-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6f551-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f551-109">備註</span><span class="sxs-lookup"><span data-stu-id="6f551-109">Remarks</span></span>  

 <span data-ttu-id="6f551-110">一旦關閉範圍，就不能在其中定義任何變數。</span><span class="sxs-lookup"><span data-stu-id="6f551-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="6f551-111">[ISymUnmanagedWriter：： OpenScope](isymunmanagedwriter-openscope-method.md) 會傳回不透明的範圍識別碼，這個識別碼可以搭配 [ISymUnmanagedWriter：： SetScopeRange](isymunmanagedwriter-setscoperange-method.md) 使用，以便於稍後定義範圍的起始和結束位移。</span><span class="sxs-lookup"><span data-stu-id="6f551-111">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="6f551-112">在這種情況下，傳遞到 `ISymUnmanagedWriter::OpenScope` 和 `ISymUnmanagedWriter::CloseScope` 的位移會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6f551-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="6f551-113">範圍識別碼只有在目前方法中才有效。</span><span class="sxs-lookup"><span data-stu-id="6f551-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f551-114">需求</span><span class="sxs-lookup"><span data-stu-id="6f551-114">Requirements</span></span>  

 <span data-ttu-id="6f551-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6f551-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f551-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f551-116">See also</span></span>

- [<span data-ttu-id="6f551-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="6f551-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
