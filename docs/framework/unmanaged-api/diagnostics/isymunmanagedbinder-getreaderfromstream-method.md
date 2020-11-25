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
ms.openlocfilehash: 2d927b02b7deebecb53a2218e2ec0275a07307b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706953"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="ef035-102">ISymUnmanagedBinder::GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="ef035-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>

<span data-ttu-id="ef035-103">指定中繼資料介面和包含符號存放區的資料流程時，會傳回正確的 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 結構，以便從指定的符號存放區讀取偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="ef035-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef035-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef035-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef035-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef035-105">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="ef035-106">在中繼資料匯入介面的指標。</span><span class="sxs-lookup"><span data-stu-id="ef035-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="ef035-107">在包含符號存放區之資料流程的指標。</span><span class="sxs-lookup"><span data-stu-id="ef035-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ef035-108">擴展設定為傳回之 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="ef035-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef035-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef035-109">Return Value</span></span>  

 <span data-ttu-id="ef035-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ef035-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef035-111">需求</span><span class="sxs-lookup"><span data-stu-id="ef035-111">Requirements</span></span>  

 <span data-ttu-id="ef035-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ef035-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef035-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef035-113">See also</span></span>

- [<span data-ttu-id="ef035-114">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="ef035-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
