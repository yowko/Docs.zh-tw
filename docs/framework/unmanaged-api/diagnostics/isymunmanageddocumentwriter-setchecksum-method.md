---
title: "ISymUnmanagedDocumentWriter::SetCheckSum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e4f653ab7b2a1341af8917c6932ea8bdfd64d83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="e2b5f-102">ISymUnmanagedDocumentWriter::SetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="e2b5f-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="e2b5f-103">設定總和檢查碼資訊。</span><span class="sxs-lookup"><span data-stu-id="e2b5f-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2b5f-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2b5f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2b5f-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="e2b5f-106">[in]GUID，代表演算法識別項。</span><span class="sxs-lookup"><span data-stu-id="e2b5f-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="e2b5f-107">[in]A`ULONG32`指出的大小，以位元組為單位，`checkSum`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e2b5f-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="e2b5f-108">[in]儲存的總和檢查碼資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e2b5f-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2b5f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e2b5f-109">Return Value</span></span>  
 <span data-ttu-id="e2b5f-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2b5f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2b5f-111">需求</span><span class="sxs-lookup"><span data-stu-id="e2b5f-111">Requirements</span></span>  
 <span data-ttu-id="e2b5f-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e2b5f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b5f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2b5f-113">See Also</span></span>  
 [<span data-ttu-id="e2b5f-114">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="e2b5f-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
