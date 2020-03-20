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
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176626"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="48ded-102">ISymENCUnmanagedMethod::GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="48ded-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="48ded-103">獲取此方法中具有行的文檔。</span><span class="sxs-lookup"><span data-stu-id="48ded-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ded-104">語法</span><span class="sxs-lookup"><span data-stu-id="48ded-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48ded-105">參數</span><span class="sxs-lookup"><span data-stu-id="48ded-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="48ded-106">[在]指向 的緩衝區的長度`pcDocs`。</span><span class="sxs-lookup"><span data-stu-id="48ded-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="48ded-107">[出]指向 的指標`ULONG32`，該指標接收包含文檔所需的緩衝區的大小（以字元表示）。</span><span class="sxs-lookup"><span data-stu-id="48ded-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="48ded-108">[在]包含文檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="48ded-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48ded-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="48ded-109">Return Value</span></span>  
 <span data-ttu-id="48ded-110">如果方法成功，S_OK;否則，錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="48ded-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48ded-111">需求</span><span class="sxs-lookup"><span data-stu-id="48ded-111">Requirements</span></span>  
 <span data-ttu-id="48ded-112">**標題：** 科西姆.伊德爾，科西姆.h</span><span class="sxs-lookup"><span data-stu-id="48ded-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ded-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48ded-113">See also</span></span>

- [<span data-ttu-id="48ded-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="48ded-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
