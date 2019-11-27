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
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427873"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="fcdda-102">ISymUnmanagedWriter::SetMethodSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="fcdda-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="fcdda-103">指定原始檔中方法的 true 開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="fcdda-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="fcdda-104">您可以使用這個方法來指定方法的範圍，而不受存在於方法內的序列點。</span><span class="sxs-lookup"><span data-stu-id="fcdda-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcdda-105">語法</span><span class="sxs-lookup"><span data-stu-id="fcdda-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcdda-106">參數</span><span class="sxs-lookup"><span data-stu-id="fcdda-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="fcdda-107">在包含開始位置之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="fcdda-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="fcdda-108">在起始行號。</span><span class="sxs-lookup"><span data-stu-id="fcdda-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="fcdda-109">在起始資料行。</span><span class="sxs-lookup"><span data-stu-id="fcdda-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="fcdda-110">在包含結束位置之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="fcdda-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="fcdda-111">在結束行號。</span><span class="sxs-lookup"><span data-stu-id="fcdda-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="fcdda-112">在結束欄號。</span><span class="sxs-lookup"><span data-stu-id="fcdda-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcdda-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="fcdda-113">Return Value</span></span>  
 <span data-ttu-id="fcdda-114">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fcdda-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcdda-115">需求</span><span class="sxs-lookup"><span data-stu-id="fcdda-115">Requirements</span></span>  
 <span data-ttu-id="fcdda-116">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="fcdda-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdda-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="fcdda-117">See also</span></span>

- [<span data-ttu-id="fcdda-118">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="fcdda-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
