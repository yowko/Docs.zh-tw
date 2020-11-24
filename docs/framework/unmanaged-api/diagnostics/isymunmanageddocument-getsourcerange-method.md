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
ms.openlocfilehash: f5d7df60a7b9c728b73fe6592226a8b6734b1e66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692146"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="7bc61-102">ISymUnmanagedDocument::GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="7bc61-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>

<span data-ttu-id="7bc61-103">將內嵌來源的指定範圍傳回至指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7bc61-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="7bc61-104">緩衝區必須夠大，才能容納來源。</span><span class="sxs-lookup"><span data-stu-id="7bc61-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bc61-105">語法</span><span class="sxs-lookup"><span data-stu-id="7bc61-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7bc61-106">參數</span><span class="sxs-lookup"><span data-stu-id="7bc61-106">Parameters</span></span>  

 `startLine`  
 <span data-ttu-id="7bc61-107">在目前檔中的起始行。</span><span class="sxs-lookup"><span data-stu-id="7bc61-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="7bc61-108">在目前檔中的起始資料行。</span><span class="sxs-lookup"><span data-stu-id="7bc61-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="7bc61-109">在目前檔中的最後一行。</span><span class="sxs-lookup"><span data-stu-id="7bc61-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="7bc61-110">在目前檔中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="7bc61-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="7bc61-111">在來源的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7bc61-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="7bc61-112">擴展接收來源大小之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="7bc61-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="7bc61-113">擴展來源文件指定範圍的大小和長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7bc61-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bc61-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="7bc61-114">Return Value</span></span>  

 <span data-ttu-id="7bc61-115">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7bc61-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bc61-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bc61-116">See also</span></span>

- [<span data-ttu-id="7bc61-117">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="7bc61-117">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
