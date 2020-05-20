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
ms.openlocfilehash: 4ba3f31ae6d6b67d7beaa2f709bf6174b721136d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609517"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="efe03-102">ISymUnmanagedWriter::SetMethodSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="efe03-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="efe03-103">指定原始程式檔內方法的實際開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="efe03-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="efe03-104">您可以使用這個方法來指定方法的範圍，而不受存在於方法內的序列點。</span><span class="sxs-lookup"><span data-stu-id="efe03-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe03-105">語法</span><span class="sxs-lookup"><span data-stu-id="efe03-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efe03-106">參數</span><span class="sxs-lookup"><span data-stu-id="efe03-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="efe03-107">在包含開始位置之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="efe03-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="efe03-108">在起始行號。</span><span class="sxs-lookup"><span data-stu-id="efe03-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="efe03-109">在起始資料行。</span><span class="sxs-lookup"><span data-stu-id="efe03-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="efe03-110">在包含結束位置之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="efe03-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="efe03-111">在結束行號。</span><span class="sxs-lookup"><span data-stu-id="efe03-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="efe03-112">在結束欄號。</span><span class="sxs-lookup"><span data-stu-id="efe03-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efe03-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="efe03-113">Return Value</span></span>  
 <span data-ttu-id="efe03-114">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="efe03-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe03-115">需求</span><span class="sxs-lookup"><span data-stu-id="efe03-115">Requirements</span></span>  
 <span data-ttu-id="efe03-116">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="efe03-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe03-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efe03-117">See also</span></span>

- [<span data-ttu-id="efe03-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="efe03-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
