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
ms.openlocfilehash: f3c7f7e06822f419282209ac39d4cbd46e600a66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424985"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="5fe62-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="5fe62-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="5fe62-103">取得這個方法有行中的文件數目。</span><span class="sxs-lookup"><span data-stu-id="5fe62-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe62-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fe62-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fe62-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fe62-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5fe62-106">[out]指標`ULONG32`包含文件所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="5fe62-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fe62-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5fe62-107">Return Value</span></span>  
 <span data-ttu-id="5fe62-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5fe62-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe62-109">需求</span><span class="sxs-lookup"><span data-stu-id="5fe62-109">Requirements</span></span>  
 <span data-ttu-id="5fe62-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5fe62-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe62-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fe62-111">See Also</span></span>  
 [<span data-ttu-id="5fe62-112">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="5fe62-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
