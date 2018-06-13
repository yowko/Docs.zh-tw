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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b9b77b94e466a4aab4a575501ac6922293b3410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424140"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="e9acb-102">ISymUnmanagedDocumentWriter::SetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="e9acb-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="e9acb-103">設定總和檢查碼資訊。</span><span class="sxs-lookup"><span data-stu-id="e9acb-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9acb-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9acb-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9acb-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9acb-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="e9acb-106">[in]GUID，代表演算法識別項。</span><span class="sxs-lookup"><span data-stu-id="e9acb-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="e9acb-107">[in]A`ULONG32`指出的大小，以位元組為單位，`checkSum`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e9acb-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="e9acb-108">[in]儲存的總和檢查碼資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e9acb-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9acb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9acb-109">Return Value</span></span>  
 <span data-ttu-id="e9acb-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9acb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9acb-111">需求</span><span class="sxs-lookup"><span data-stu-id="e9acb-111">Requirements</span></span>  
 <span data-ttu-id="e9acb-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e9acb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9acb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9acb-113">See Also</span></span>  
 [<span data-ttu-id="e9acb-114">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="e9acb-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
