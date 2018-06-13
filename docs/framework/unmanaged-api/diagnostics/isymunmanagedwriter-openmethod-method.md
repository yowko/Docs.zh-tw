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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc41acd6a4f2ef2557d3b39523c5e398c887c454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427904"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="6c3bb-102">ISymUnmanagedWriter::OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="6c3bb-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="6c3bb-103">開啟的符號資訊就會發出的方法。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="6c3bb-104">指定的方法會變成目前的方法呼叫來定義序列點、 參數和語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="6c3bb-105">沒有隱含的語彙範圍整個方法。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="6c3bb-106">重新開啟先前已關閉的方法，會清除任何先前定義的符號，該方法。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="6c3bb-107">一次可以有只有一個開啟的方法。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c3bb-108">語法</span><span class="sxs-lookup"><span data-stu-id="6c3bb-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c3bb-109">參數</span><span class="sxs-lookup"><span data-stu-id="6c3bb-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="6c3bb-110">[in]若要開啟方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c3bb-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c3bb-111">Return Value</span></span>  
 <span data-ttu-id="6c3bb-112">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c3bb-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c3bb-113">需求</span><span class="sxs-lookup"><span data-stu-id="6c3bb-113">Requirements</span></span>  
 <span data-ttu-id="6c3bb-114">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c3bb-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3bb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c3bb-115">See Also</span></span>  
 [<span data-ttu-id="6c3bb-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="6c3bb-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="6c3bb-117">CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="6c3bb-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="6c3bb-118">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="6c3bb-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
