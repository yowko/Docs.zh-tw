---
title: ISymUnmanagedWriter::SetMethodSourceRange 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: a918b5c2334683348adc6a7382527faedb52d7b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683533"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="3cfa5-102">ISymUnmanagedWriter::SetMethodSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="3cfa5-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>

<span data-ttu-id="3cfa5-103">指定原始程式檔內方法的實際開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="3cfa5-104">您可以使用這個方法來指定方法的範圍，而不受存在於方法內的序列點。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cfa5-105">語法</span><span class="sxs-lookup"><span data-stu-id="3cfa5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cfa5-106">參數</span><span class="sxs-lookup"><span data-stu-id="3cfa5-106">Parameters</span></span>  

 `startDoc`  
 <span data-ttu-id="3cfa5-107">在包含開始位置之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="3cfa5-108">在起始行號。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="3cfa5-109">在開始資料行。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="3cfa5-110">在包含結束位置之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="3cfa5-111">在結束行號。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="3cfa5-112">在結束資料行編號。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cfa5-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="3cfa5-113">Return Value</span></span>  

 <span data-ttu-id="3cfa5-114">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3cfa5-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cfa5-115">需求</span><span class="sxs-lookup"><span data-stu-id="3cfa5-115">Requirements</span></span>  

 <span data-ttu-id="3cfa5-116">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3cfa5-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cfa5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cfa5-117">See also</span></span>

- [<span data-ttu-id="3cfa5-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="3cfa5-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
