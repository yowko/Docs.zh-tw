---
title: ISymUnmanagedDocument::GetSourceRange 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 767508e51660a161a7a6ff0b168a46178d66be99
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474136"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="e8364-102">ISymUnmanagedDocument::GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="e8364-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="e8364-103">傳回指定的範圍的內嵌來源到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e8364-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="e8364-104">緩衝區必須夠大，無法容納來源。</span><span class="sxs-lookup"><span data-stu-id="e8364-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8364-105">語法</span><span class="sxs-lookup"><span data-stu-id="e8364-105">Syntax</span></span>  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8364-106">參數</span><span class="sxs-lookup"><span data-stu-id="e8364-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="e8364-107">[in]目前文件起始行。</span><span class="sxs-lookup"><span data-stu-id="e8364-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="e8364-108">[in]目前的文件中的起始欄。</span><span class="sxs-lookup"><span data-stu-id="e8364-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="e8364-109">[in]目前的文件中的最後一行。</span><span class="sxs-lookup"><span data-stu-id="e8364-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="e8364-110">[in]目前的文件中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="e8364-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="e8364-111">[in]來源，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="e8364-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="e8364-112">[out]此變數會接收來源的大小指標。</span><span class="sxs-lookup"><span data-stu-id="e8364-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="e8364-113">[out]大小和來源文件，以位元組為單位的指定範圍的長度。</span><span class="sxs-lookup"><span data-stu-id="e8364-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8364-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8364-114">Return Value</span></span>  
 <span data-ttu-id="e8364-115">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e8364-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8364-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8364-116">See also</span></span>
- [<span data-ttu-id="e8364-117">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="e8364-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
