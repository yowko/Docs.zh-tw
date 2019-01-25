---
title: ISymUnmanagedMethod::GetSequencePointCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8e919c546df93a2023858c31ebc4d2dec507513
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730135"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="ae635-102">ISymUnmanagedMethod::GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="ae635-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="ae635-103">取得這個方法內的序列點的計數。</span><span class="sxs-lookup"><span data-stu-id="ae635-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae635-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae635-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae635-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae635-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ae635-106">[out]指標`ULONG32`接收包含序列點所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="ae635-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae635-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae635-107">Return Value</span></span>  
 <span data-ttu-id="ae635-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae635-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae635-109">需求</span><span class="sxs-lookup"><span data-stu-id="ae635-109">Requirements</span></span>  
 <span data-ttu-id="ae635-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ae635-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae635-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae635-111">See also</span></span>
- [<span data-ttu-id="ae635-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="ae635-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
