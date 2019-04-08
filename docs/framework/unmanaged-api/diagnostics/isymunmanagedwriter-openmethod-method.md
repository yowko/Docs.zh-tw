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
ms.openlocfilehash: b05ba185a9ad4ab076d29d7d609734d41677b760
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194782"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="63dd1-102">ISymUnmanagedWriter::OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="63dd1-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="63dd1-103">開啟到的符號資訊就會發出的方法。</span><span class="sxs-lookup"><span data-stu-id="63dd1-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="63dd1-104">指定的方法會變成目前的方法，來定義序列點、 參數和語彙範圍的呼叫。</span><span class="sxs-lookup"><span data-stu-id="63dd1-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="63dd1-105">沒有隱含的語彙範圍，整個方法。</span><span class="sxs-lookup"><span data-stu-id="63dd1-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="63dd1-106">重新開啟先前已關閉的方法，就會清除任何先前定義的符號，該方法。</span><span class="sxs-lookup"><span data-stu-id="63dd1-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="63dd1-107">一次可以有只有一個開啟的方法。</span><span class="sxs-lookup"><span data-stu-id="63dd1-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63dd1-108">語法</span><span class="sxs-lookup"><span data-stu-id="63dd1-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63dd1-109">參數</span><span class="sxs-lookup"><span data-stu-id="63dd1-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="63dd1-110">[in]若要開啟方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="63dd1-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63dd1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="63dd1-111">Return Value</span></span>  
 <span data-ttu-id="63dd1-112">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="63dd1-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63dd1-113">需求</span><span class="sxs-lookup"><span data-stu-id="63dd1-113">Requirements</span></span>  
 <span data-ttu-id="63dd1-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="63dd1-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63dd1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63dd1-115">See also</span></span>

- [<span data-ttu-id="63dd1-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="63dd1-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="63dd1-117">CloseMethod 方法</span><span class="sxs-lookup"><span data-stu-id="63dd1-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="63dd1-118">OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="63dd1-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
