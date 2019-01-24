---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c13fc4270b44a2483c2e9aabaedcf8f0668d2e7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743916"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="c52bc-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="c52bc-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="c52bc-103">取得這個方法有幾行中的文件數目。</span><span class="sxs-lookup"><span data-stu-id="c52bc-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c52bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="c52bc-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c52bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="c52bc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c52bc-106">[out]指標`ULONG32`接收包含文件所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c52bc-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c52bc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c52bc-107">Return Value</span></span>  
 <span data-ttu-id="c52bc-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c52bc-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c52bc-109">需求</span><span class="sxs-lookup"><span data-stu-id="c52bc-109">Requirements</span></span>  
 <span data-ttu-id="c52bc-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c52bc-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52bc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c52bc-111">See also</span></span>
- [<span data-ttu-id="c52bc-112">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c52bc-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
