---
title: ISymUnmanagedWriter::OpenMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: 7b13ca9884516e95e0bb922efc5bc1a845344e38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427927"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="feded-102">ISymUnmanagedWriter::OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="feded-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="feded-103">開啟用來發出符號資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="feded-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="feded-104">給定的方法會成為呼叫的目前方法，以定義序列點、參數和詞彙範圍。</span><span class="sxs-lookup"><span data-stu-id="feded-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="feded-105">整個方法周圍有隱含的詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="feded-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="feded-106">重新開啟先前已關閉的方法，會清除該方法先前定義的任何符號。</span><span class="sxs-lookup"><span data-stu-id="feded-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="feded-107">一次只能有一個開啟的方法。</span><span class="sxs-lookup"><span data-stu-id="feded-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feded-108">語法</span><span class="sxs-lookup"><span data-stu-id="feded-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feded-109">參數</span><span class="sxs-lookup"><span data-stu-id="feded-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="feded-110">在要開啟之方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="feded-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feded-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="feded-111">Return Value</span></span>  
 <span data-ttu-id="feded-112">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="feded-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feded-113">需求</span><span class="sxs-lookup"><span data-stu-id="feded-113">Requirements</span></span>  
 <span data-ttu-id="feded-114">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="feded-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feded-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feded-115">See also</span></span>

- [<span data-ttu-id="feded-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="feded-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="feded-117">CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="feded-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="feded-118">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="feded-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
