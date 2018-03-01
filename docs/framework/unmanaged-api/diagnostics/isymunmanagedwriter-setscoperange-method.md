---
title: "ISymUnmanagedWriter::SetScopeRange 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9afb0038adc4273033fb9f1db1ebc57f43eae779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="b5301-102">ISymUnmanagedWriter::SetScopeRange 方法</span><span class="sxs-lookup"><span data-stu-id="b5301-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="b5301-103">定義指定語彙範圍的位移範圍。</span><span class="sxs-lookup"><span data-stu-id="b5301-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="b5301-104">範圍會變成新的目前範圍，並且推送至堆疊的範圍。</span><span class="sxs-lookup"><span data-stu-id="b5301-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="b5301-105">範圍必須形成階層。</span><span class="sxs-lookup"><span data-stu-id="b5301-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="b5301-106">同層級不允許重疊。</span><span class="sxs-lookup"><span data-stu-id="b5301-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5301-107">語法</span><span class="sxs-lookup"><span data-stu-id="b5301-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5301-108">參數</span><span class="sxs-lookup"><span data-stu-id="b5301-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="b5301-109">[in]範圍識別項的範圍。</span><span class="sxs-lookup"><span data-stu-id="b5301-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="b5301-110">[in]以位元組為單位，從頭語彙範圍中方法的第一個指令的位移。</span><span class="sxs-lookup"><span data-stu-id="b5301-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b5301-111">[in]位移，以位元組為單位從頭語彙範圍中最後一個指令的方法。</span><span class="sxs-lookup"><span data-stu-id="b5301-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5301-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b5301-112">Return Value</span></span>  
 <span data-ttu-id="b5301-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b5301-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5301-114">備註</span><span class="sxs-lookup"><span data-stu-id="b5301-114">Remarks</span></span>  
 <span data-ttu-id="b5301-115">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)傳回不透明範圍識別項，可以搭配`ISymUnmanagedWriter::SetScopeRange`定義範圍的開始和結束位移的稍後時間。</span><span class="sxs-lookup"><span data-stu-id="b5301-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="b5301-116">在此情況下，位移傳遞到`ISymUnmanagedWriter::OpenScope`和[isymunmanagedwriter:: Closescope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b5301-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="b5301-117">範圍識別項，才有效目前方法中。</span><span class="sxs-lookup"><span data-stu-id="b5301-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5301-118">需求</span><span class="sxs-lookup"><span data-stu-id="b5301-118">Requirements</span></span>  
 <span data-ttu-id="b5301-119">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5301-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5301-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5301-120">See Also</span></span>  
 [<span data-ttu-id="b5301-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b5301-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
