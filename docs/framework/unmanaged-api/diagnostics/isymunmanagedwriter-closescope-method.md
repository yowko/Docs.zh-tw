---
title: "ISymUnmanagedWriter::CloseScope 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8df22e5f9ea2ca294f502fcebf4b2ed5cd7900d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="afd62-102">ISymUnmanagedWriter::CloseScope 方法</span><span class="sxs-lookup"><span data-stu-id="afd62-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="afd62-103">關閉目前的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="afd62-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd62-104">語法</span><span class="sxs-lookup"><span data-stu-id="afd62-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afd62-105">參數</span><span class="sxs-lookup"><span data-stu-id="afd62-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="afd62-106">[in]從之方法的語彙範圍，以位元組為單位中的最後一個指令結尾的點開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="afd62-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afd62-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="afd62-107">Return Value</span></span>  
 <span data-ttu-id="afd62-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="afd62-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afd62-109">備註</span><span class="sxs-lookup"><span data-stu-id="afd62-109">Remarks</span></span>  
 <span data-ttu-id="afd62-110">一旦關閉範圍，可以定義其他變數內。</span><span class="sxs-lookup"><span data-stu-id="afd62-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="afd62-111">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)傳回不透明範圍識別項，可以搭配[isymunmanagedwriter:: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)稍後定義範圍的開始和結束位移。</span><span class="sxs-lookup"><span data-stu-id="afd62-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="afd62-112">在這種情況下，傳遞到 `ISymUnmanagedWriter::OpenScope` 和 `ISymUnmanagedWriter::CloseScope` 的位移會被忽略。</span><span class="sxs-lookup"><span data-stu-id="afd62-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="afd62-113">範圍識別項會在目前的方法中才有效。</span><span class="sxs-lookup"><span data-stu-id="afd62-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afd62-114">需求</span><span class="sxs-lookup"><span data-stu-id="afd62-114">Requirements</span></span>  
 <span data-ttu-id="afd62-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="afd62-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd62-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afd62-116">See Also</span></span>  
 [<span data-ttu-id="afd62-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="afd62-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
