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
ms.openlocfilehash: 59ec4d9f39362f563312a9ed75bb1ab5cede799d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484026"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="8a566-102">ISymUnmanagedDocumentWriter::SetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="8a566-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="8a566-103">設定總和檢查碼資訊。</span><span class="sxs-lookup"><span data-stu-id="8a566-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a566-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a566-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a566-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a566-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="8a566-106">[in]GUID，表示演算法識別項。</span><span class="sxs-lookup"><span data-stu-id="8a566-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="8a566-107">[in]A`ULONG32`表示的大小，以位元組為單位，`checkSum`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8a566-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="8a566-108">[in]儲存的總和檢查碼資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8a566-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a566-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a566-109">Return Value</span></span>  
 <span data-ttu-id="8a566-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a566-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a566-111">需求</span><span class="sxs-lookup"><span data-stu-id="8a566-111">Requirements</span></span>  
 <span data-ttu-id="8a566-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8a566-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a566-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a566-113">See also</span></span>
- [<span data-ttu-id="8a566-114">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="8a566-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
