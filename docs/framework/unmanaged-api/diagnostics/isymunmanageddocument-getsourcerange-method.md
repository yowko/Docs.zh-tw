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
ms.openlocfilehash: 59420cfd29c3228aece9fc5ae02b950db6099ea0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218468"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="ef6e5-102">ISymUnmanagedDocument::GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="ef6e5-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="ef6e5-103">傳回指定的範圍的內嵌來源到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="ef6e5-104">緩衝區必須夠大，無法容納來源。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef6e5-105">語法</span><span class="sxs-lookup"><span data-stu-id="ef6e5-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ef6e5-106">參數</span><span class="sxs-lookup"><span data-stu-id="ef6e5-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="ef6e5-107">[in]目前文件起始行。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="ef6e5-108">[in]目前的文件中的起始欄。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="ef6e5-109">[in]目前的文件中的最後一行。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="ef6e5-110">[in]目前的文件中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="ef6e5-111">[in]來源，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="ef6e5-112">[out]此變數會接收來源的大小指標。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="ef6e5-113">[out]大小和來源文件，以位元組為單位的指定範圍的長度。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef6e5-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef6e5-114">Return Value</span></span>  
 <span data-ttu-id="ef6e5-115">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ef6e5-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6e5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef6e5-116">See also</span></span>

- [<span data-ttu-id="ef6e5-117">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="ef6e5-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
