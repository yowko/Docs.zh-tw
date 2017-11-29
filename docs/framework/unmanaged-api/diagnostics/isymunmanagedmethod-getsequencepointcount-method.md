---
title: "ISymUnmanagedMethod::GetSequencePointCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePointCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1666eacd8756209c126171ad8ecae56afa802892
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="5a05c-102">ISymUnmanagedMethod::GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="5a05c-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="5a05c-103">取得這個方法內的序列點的計數。</span><span class="sxs-lookup"><span data-stu-id="5a05c-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a05c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a05c-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a05c-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a05c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5a05c-106">[out]指標`ULONG32`包含序列點所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="5a05c-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a05c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a05c-107">Return Value</span></span>  
 <span data-ttu-id="5a05c-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a05c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a05c-109">需求</span><span class="sxs-lookup"><span data-stu-id="5a05c-109">Requirements</span></span>  
 <span data-ttu-id="5a05c-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a05c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a05c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a05c-111">See Also</span></span>  
 [<span data-ttu-id="5a05c-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="5a05c-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
