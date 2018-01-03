---
title: "ISymUnmanagedWriter::SetMethodSourceRange 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetMethodSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f82be130dba8087cf649d3e89bec8afc065e86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="79ca9-102">ISymUnmanagedWriter::SetMethodSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="79ca9-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="79ca9-103">指定的則為 true 的開始和結束的原始程式檔內的方法。</span><span class="sxs-lookup"><span data-stu-id="79ca9-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="79ca9-104">使用此方法可指定的方法，以獨立存在的方法內的序列點的範圍。</span><span class="sxs-lookup"><span data-stu-id="79ca9-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ca9-105">語法</span><span class="sxs-lookup"><span data-stu-id="79ca9-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79ca9-106">參數</span><span class="sxs-lookup"><span data-stu-id="79ca9-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="79ca9-107">[in]包含開始位置的文件指標。</span><span class="sxs-lookup"><span data-stu-id="79ca9-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="79ca9-108">[in]起始行號。</span><span class="sxs-lookup"><span data-stu-id="79ca9-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="79ca9-109">[in]起始的資料行。</span><span class="sxs-lookup"><span data-stu-id="79ca9-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="79ca9-110">[in]包含的結束位置的文件指標。</span><span class="sxs-lookup"><span data-stu-id="79ca9-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="79ca9-111">[in]結束的行號。</span><span class="sxs-lookup"><span data-stu-id="79ca9-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="79ca9-112">[in]結束資料行數目。</span><span class="sxs-lookup"><span data-stu-id="79ca9-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79ca9-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="79ca9-113">Return Value</span></span>  
 <span data-ttu-id="79ca9-114">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="79ca9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79ca9-115">需求</span><span class="sxs-lookup"><span data-stu-id="79ca9-115">Requirements</span></span>  
 <span data-ttu-id="79ca9-116">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="79ca9-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ca9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="79ca9-117">See Also</span></span>  
 [<span data-ttu-id="79ca9-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="79ca9-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
