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
ms.openlocfilehash: 49023424c21fced1c49b16ecdbea93c654b5e883
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448378"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="84178-102">ISymENCUnmanagedMethod::GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="84178-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="84178-103">取得此方法在中具有行的檔。</span><span class="sxs-lookup"><span data-stu-id="84178-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84178-104">語法</span><span class="sxs-lookup"><span data-stu-id="84178-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84178-105">參數</span><span class="sxs-lookup"><span data-stu-id="84178-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="84178-106">在`pcDocs`所指向之緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="84178-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="84178-107">脫銷`ULONG32` 的指標，接收包含檔所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="84178-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="84178-108">在包含檔的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="84178-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84178-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="84178-109">Return Value</span></span>  
 <span data-ttu-id="84178-110">如果方法成功，則 S_OK;否則，錯誤碼為。</span><span class="sxs-lookup"><span data-stu-id="84178-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84178-111">需求</span><span class="sxs-lookup"><span data-stu-id="84178-111">Requirements</span></span>  
 <span data-ttu-id="84178-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="84178-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84178-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84178-113">See also</span></span>

- [<span data-ttu-id="84178-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="84178-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
