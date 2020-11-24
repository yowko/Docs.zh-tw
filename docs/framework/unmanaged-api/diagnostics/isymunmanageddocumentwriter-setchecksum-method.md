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
ms.openlocfilehash: 58055d9ea56d7928729d289198965752985d8e0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688896"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="d1927-102">ISymUnmanagedDocumentWriter::SetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="d1927-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="d1927-103">設定總和檢查碼資訊。</span><span class="sxs-lookup"><span data-stu-id="d1927-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1927-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1927-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1927-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1927-105">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="d1927-106">在表示演算法識別碼的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d1927-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="d1927-107">在， `ULONG32` 表示緩衝區的大小（以位元組為單位） `checkSum` 。</span><span class="sxs-lookup"><span data-stu-id="d1927-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="d1927-108">在儲存總和檢查碼資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d1927-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1927-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1927-109">Return Value</span></span>  

 <span data-ttu-id="d1927-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d1927-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1927-111">需求</span><span class="sxs-lookup"><span data-stu-id="d1927-111">Requirements</span></span>  

 <span data-ttu-id="d1927-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d1927-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1927-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1927-113">See also</span></span>

- [<span data-ttu-id="d1927-114">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d1927-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
