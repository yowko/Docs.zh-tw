---
title: "ISymUnmanagedWriter::OpenMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6cfb41748861150b28493c835e80135abe90826
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="63bd5-102">ISymUnmanagedWriter::OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="63bd5-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="63bd5-103">開啟的符號資訊就會發出的方法。</span><span class="sxs-lookup"><span data-stu-id="63bd5-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="63bd5-104">指定的方法會變成目前的方法呼叫來定義序列點、 參數和語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="63bd5-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="63bd5-105">沒有隱含的語彙範圍整個方法。</span><span class="sxs-lookup"><span data-stu-id="63bd5-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="63bd5-106">重新開啟先前已關閉的方法，會清除任何先前定義的符號，該方法。</span><span class="sxs-lookup"><span data-stu-id="63bd5-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="63bd5-107">一次可以有只有一個開啟的方法。</span><span class="sxs-lookup"><span data-stu-id="63bd5-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63bd5-108">語法</span><span class="sxs-lookup"><span data-stu-id="63bd5-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63bd5-109">參數</span><span class="sxs-lookup"><span data-stu-id="63bd5-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="63bd5-110">[in]若要開啟方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="63bd5-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63bd5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="63bd5-111">Return Value</span></span>  
 <span data-ttu-id="63bd5-112">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="63bd5-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63bd5-113">需求</span><span class="sxs-lookup"><span data-stu-id="63bd5-113">Requirements</span></span>  
 <span data-ttu-id="63bd5-114">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="63bd5-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bd5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="63bd5-115">See Also</span></span>  
 [<span data-ttu-id="63bd5-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="63bd5-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="63bd5-117">CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="63bd5-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="63bd5-118">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="63bd5-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
