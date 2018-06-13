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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a11f689f1fa93e1122ffcc78187c4287db7ea534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427020"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="8e680-102">ISymUnmanagedWriter::CloseScope 方法</span><span class="sxs-lookup"><span data-stu-id="8e680-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="8e680-103">關閉目前的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="8e680-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e680-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e680-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e680-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e680-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="8e680-106">[in]從之方法的語彙範圍，以位元組為單位中的最後一個指令結尾的點開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="8e680-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e680-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e680-107">Return Value</span></span>  
 <span data-ttu-id="8e680-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e680-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e680-109">備註</span><span class="sxs-lookup"><span data-stu-id="8e680-109">Remarks</span></span>  
 <span data-ttu-id="8e680-110">一旦關閉範圍，可以定義其他變數內。</span><span class="sxs-lookup"><span data-stu-id="8e680-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="8e680-111">[Isymunmanagedwriter:: Openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)傳回不透明範圍識別項，可以搭配[isymunmanagedwriter:: Setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)稍後定義範圍的開始和結束位移。</span><span class="sxs-lookup"><span data-stu-id="8e680-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="8e680-112">在這種情況下，傳遞到 `ISymUnmanagedWriter::OpenScope` 和 `ISymUnmanagedWriter::CloseScope` 的位移會被忽略。</span><span class="sxs-lookup"><span data-stu-id="8e680-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="8e680-113">範圍識別項會在目前的方法中才有效。</span><span class="sxs-lookup"><span data-stu-id="8e680-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e680-114">需求</span><span class="sxs-lookup"><span data-stu-id="8e680-114">Requirements</span></span>  
 <span data-ttu-id="8e680-115">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8e680-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e680-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e680-116">See Also</span></span>  
 [<span data-ttu-id="8e680-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="8e680-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
