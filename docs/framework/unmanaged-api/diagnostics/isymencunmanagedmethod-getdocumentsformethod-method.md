---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b329d096a23df673de038036fa5ea196cbe0eac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736067"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="6cf80-102">ISymENCUnmanagedMethod::GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="6cf80-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="6cf80-103">取得這個方法有幾行中的文件。</span><span class="sxs-lookup"><span data-stu-id="6cf80-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf80-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cf80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cf80-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cf80-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="6cf80-106">[in]所指向緩衝區的長度`pcDocs`。</span><span class="sxs-lookup"><span data-stu-id="6cf80-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="6cf80-107">[out]指標`ULONG32`接收大小，以字元為單位，包含文件所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6cf80-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="6cf80-108">[in]包含文件的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6cf80-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cf80-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6cf80-109">Return Value</span></span>  
 <span data-ttu-id="6cf80-110">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="6cf80-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cf80-111">需求</span><span class="sxs-lookup"><span data-stu-id="6cf80-111">Requirements</span></span>  
 <span data-ttu-id="6cf80-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6cf80-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf80-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf80-113">See also</span></span>

- [<span data-ttu-id="6cf80-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="6cf80-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
