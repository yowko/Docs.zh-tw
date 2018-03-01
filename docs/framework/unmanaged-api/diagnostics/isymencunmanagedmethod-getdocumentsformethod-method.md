---
title: "ISymENCUnmanagedMethod::GetDocumentsForMethod 方法"
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
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0593ea430d27641a57705f1ceb4805ab505ef25e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="613e0-102">ISymENCUnmanagedMethod::GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="613e0-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="613e0-103">取得這個方法有行中的文件。</span><span class="sxs-lookup"><span data-stu-id="613e0-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="613e0-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="613e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="613e0-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="613e0-106">[in]所指向之緩衝區的長度`pcDocs`。</span><span class="sxs-lookup"><span data-stu-id="613e0-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="613e0-107">[out]指標`ULONG32`接收以字元為單位，包含文件所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="613e0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="613e0-108">[in]包含文件的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="613e0-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="613e0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="613e0-109">Return Value</span></span>  
 <span data-ttu-id="613e0-110">如果方法成功則為 S_OK否則，錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="613e0-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="613e0-111">需求</span><span class="sxs-lookup"><span data-stu-id="613e0-111">Requirements</span></span>  
 <span data-ttu-id="613e0-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="613e0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="613e0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="613e0-113">See Also</span></span>  
 [<span data-ttu-id="613e0-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="613e0-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
