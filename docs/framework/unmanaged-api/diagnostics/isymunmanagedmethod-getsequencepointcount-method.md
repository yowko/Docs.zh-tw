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
ms.openlocfilehash: c1a9ef59cfe63ba745e6f5eba3ba2c3f3f983886
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425388"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="368f6-102">ISymUnmanagedMethod::GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="368f6-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="368f6-103">取得這個方法內的序列點的計數。</span><span class="sxs-lookup"><span data-stu-id="368f6-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="368f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="368f6-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="368f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="368f6-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="368f6-106">[out]指標`ULONG32`包含序列點所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="368f6-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="368f6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="368f6-107">Return Value</span></span>  
 <span data-ttu-id="368f6-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="368f6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="368f6-109">需求</span><span class="sxs-lookup"><span data-stu-id="368f6-109">Requirements</span></span>  
 <span data-ttu-id="368f6-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="368f6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368f6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="368f6-111">See Also</span></span>  
 [<span data-ttu-id="368f6-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="368f6-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
