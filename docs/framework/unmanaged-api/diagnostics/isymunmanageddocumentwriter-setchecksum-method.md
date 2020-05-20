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
ms.openlocfilehash: 06a331e24622e0a155d974ca869818a6532baa1f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615536"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="fdb35-102">ISymUnmanagedDocumentWriter::SetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="fdb35-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="fdb35-103">設定總和檢查碼資訊。</span><span class="sxs-lookup"><span data-stu-id="fdb35-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb35-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdb35-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdb35-105">參數</span><span class="sxs-lookup"><span data-stu-id="fdb35-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="fdb35-106">在表示演算法識別碼的 GUID。</span><span class="sxs-lookup"><span data-stu-id="fdb35-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="fdb35-107">在`ULONG32`，表示緩衝區的大小（以位元組為單位） `checkSum` 。</span><span class="sxs-lookup"><span data-stu-id="fdb35-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="fdb35-108">在儲存總和檢查碼資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fdb35-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdb35-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="fdb35-109">Return Value</span></span>  
 <span data-ttu-id="fdb35-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fdb35-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb35-111">需求</span><span class="sxs-lookup"><span data-stu-id="fdb35-111">Requirements</span></span>  
 <span data-ttu-id="fdb35-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="fdb35-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb35-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdb35-113">See also</span></span>

- [<span data-ttu-id="fdb35-114">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="fdb35-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
