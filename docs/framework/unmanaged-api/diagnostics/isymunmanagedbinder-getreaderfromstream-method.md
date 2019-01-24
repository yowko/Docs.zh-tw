---
title: ISymUnmanagedBinder::GetReaderFromStream 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af4e9124140c2b311fb2c10800200f5d4d8dc679
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545760"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="ab412-102">ISymUnmanagedBinder::GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="ab412-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="ab412-103">提供中繼資料介面並包含符號存放區的資料流，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)指定的符號存放區的結構，將讀取偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="ab412-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab412-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab412-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab412-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab412-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="ab412-106">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="ab412-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="ab412-107">[in]包含符號存放區的資料流指標。</span><span class="sxs-lookup"><span data-stu-id="ab412-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ab412-108">[out]設定指標所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ab412-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab412-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab412-109">Return Value</span></span>  
 <span data-ttu-id="ab412-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab412-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab412-111">需求</span><span class="sxs-lookup"><span data-stu-id="ab412-111">Requirements</span></span>  
 <span data-ttu-id="ab412-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab412-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab412-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab412-113">See also</span></span>
- [<span data-ttu-id="ab412-114">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="ab412-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
