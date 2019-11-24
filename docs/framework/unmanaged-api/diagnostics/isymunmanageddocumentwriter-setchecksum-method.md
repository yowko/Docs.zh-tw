---
title: ISymUnmanagedDocumentWriter::SetCheckSum 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: dbf876a514ce106c566a168f688eb3a22d3a1ea2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449041"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="795c4-102">ISymUnmanagedDocumentWriter::SetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="795c4-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="795c4-103">設定總和檢查碼資訊。</span><span class="sxs-lookup"><span data-stu-id="795c4-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="795c4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="795c4-105">參數</span><span class="sxs-lookup"><span data-stu-id="795c4-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="795c4-106">[in] The GUID that represents the algorithm identifier.</span><span class="sxs-lookup"><span data-stu-id="795c4-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="795c4-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span><span class="sxs-lookup"><span data-stu-id="795c4-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="795c4-108">[in] The buffer that stores the checksum information.</span><span class="sxs-lookup"><span data-stu-id="795c4-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="795c4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="795c4-109">Return Value</span></span>  
 <span data-ttu-id="795c4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="795c4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795c4-111">需求</span><span class="sxs-lookup"><span data-stu-id="795c4-111">Requirements</span></span>  
 <span data-ttu-id="795c4-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="795c4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795c4-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="795c4-113">See also</span></span>

- [<span data-ttu-id="795c4-114">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="795c4-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
