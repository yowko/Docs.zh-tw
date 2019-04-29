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
ms.openlocfilehash: 9eac17ec9599caba88ddaa73d28abcae538a4d19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939577"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="1afe2-102">ISymUnmanagedMethod::GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="1afe2-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="1afe2-103">取得這個方法內的序列點的計數。</span><span class="sxs-lookup"><span data-stu-id="1afe2-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afe2-104">語法</span><span class="sxs-lookup"><span data-stu-id="1afe2-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1afe2-105">參數</span><span class="sxs-lookup"><span data-stu-id="1afe2-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1afe2-106">[out]指標`ULONG32`接收包含序列點所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="1afe2-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1afe2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1afe2-107">Return Value</span></span>  
 <span data-ttu-id="1afe2-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1afe2-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1afe2-109">需求</span><span class="sxs-lookup"><span data-stu-id="1afe2-109">Requirements</span></span>  
 <span data-ttu-id="1afe2-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1afe2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afe2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1afe2-111">See also</span></span>

- [<span data-ttu-id="1afe2-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="1afe2-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
