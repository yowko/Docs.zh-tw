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
ms.openlocfilehash: 351bb2a1eb03684a0498fba35270e1bda44a93c0
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441743"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="96e24-102">ISymUnmanagedBinder::GetReaderFromStream 方法</span><span class="sxs-lookup"><span data-stu-id="96e24-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="96e24-103">假設中繼資料介面和包含符號存放區的資料流程，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)結構，以便從指定的符號存放區讀取偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="96e24-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e24-104">語法</span><span class="sxs-lookup"><span data-stu-id="96e24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e24-105">參數</span><span class="sxs-lookup"><span data-stu-id="96e24-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="96e24-106">在中繼資料匯入介面的指標。</span><span class="sxs-lookup"><span data-stu-id="96e24-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="96e24-107">在包含符號存放區之資料流程的指標。</span><span class="sxs-lookup"><span data-stu-id="96e24-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="96e24-108">脫銷設定為所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="96e24-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96e24-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="96e24-109">Return Value</span></span>  
 <span data-ttu-id="96e24-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="96e24-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e24-111">需求</span><span class="sxs-lookup"><span data-stu-id="96e24-111">Requirements</span></span>  
 <span data-ttu-id="96e24-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="96e24-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e24-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96e24-113">See also</span></span>

- [<span data-ttu-id="96e24-114">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="96e24-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
