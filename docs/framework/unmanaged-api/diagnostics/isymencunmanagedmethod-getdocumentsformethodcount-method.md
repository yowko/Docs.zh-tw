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
ms.openlocfilehash: d096101189d52401c407a4108c9c81e201d3f30d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441938"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="3e6db-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="3e6db-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="3e6db-103">取得此方法在中具有行的檔數目。</span><span class="sxs-lookup"><span data-stu-id="3e6db-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e6db-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e6db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e6db-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e6db-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3e6db-106">脫銷的指標 `ULONG32` ，接收包含檔所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="3e6db-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e6db-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3e6db-107">Return Value</span></span>  
 <span data-ttu-id="3e6db-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3e6db-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e6db-109">需求</span><span class="sxs-lookup"><span data-stu-id="3e6db-109">Requirements</span></span>  
 <span data-ttu-id="3e6db-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3e6db-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6db-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e6db-111">See also</span></span>

- [<span data-ttu-id="3e6db-112">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="3e6db-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
