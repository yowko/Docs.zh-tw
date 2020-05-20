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
ms.openlocfilehash: 841379702e24428a8092cfd1d2cbd3c5b4e17ba4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615601"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="17828-102">ISymUnmanagedDocument::GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="17828-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="17828-103">將內嵌來源的指定範圍傳回到給定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="17828-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="17828-104">緩衝區必須夠大，才能容納來源。</span><span class="sxs-lookup"><span data-stu-id="17828-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17828-105">語法</span><span class="sxs-lookup"><span data-stu-id="17828-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="17828-106">參數</span><span class="sxs-lookup"><span data-stu-id="17828-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="17828-107">在目前檔中的起始行。</span><span class="sxs-lookup"><span data-stu-id="17828-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="17828-108">在目前檔中的起始資料行。</span><span class="sxs-lookup"><span data-stu-id="17828-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="17828-109">在目前檔中的最後一行。</span><span class="sxs-lookup"><span data-stu-id="17828-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="17828-110">在目前檔中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="17828-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="17828-111">在來源的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="17828-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="17828-112">脫銷接收來源大小之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="17828-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="17828-113">脫銷來源文件指定範圍的大小和長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="17828-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17828-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="17828-114">Return Value</span></span>  
 <span data-ttu-id="17828-115">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="17828-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17828-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17828-116">See also</span></span>

- [<span data-ttu-id="17828-117">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="17828-117">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
