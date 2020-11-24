---
title: ISymUnmanagedDocumentWriter::SetSource 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: 31475b08b569b925aab9cab869545f0912c4ecf8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691587"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="3eafa-102">ISymUnmanagedDocumentWriter::SetSource 方法</span><span class="sxs-lookup"><span data-stu-id="3eafa-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>

<span data-ttu-id="3eafa-103">設定所寫入檔的內嵌來源。</span><span class="sxs-lookup"><span data-stu-id="3eafa-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eafa-104">語法</span><span class="sxs-lookup"><span data-stu-id="3eafa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eafa-105">參數</span><span class="sxs-lookup"><span data-stu-id="3eafa-105">Parameters</span></span>  

 `sourceSize`  
 <span data-ttu-id="3eafa-106">在 `ULONG32` ，其中包含緩衝區的大小 `source` 。</span><span class="sxs-lookup"><span data-stu-id="3eafa-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="3eafa-107">在儲存內嵌來源的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3eafa-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eafa-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3eafa-108">Return Value</span></span>  

 <span data-ttu-id="3eafa-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3eafa-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eafa-110">需求</span><span class="sxs-lookup"><span data-stu-id="3eafa-110">Requirements</span></span>  

 <span data-ttu-id="3eafa-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3eafa-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eafa-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eafa-112">See also</span></span>

- [<span data-ttu-id="3eafa-113">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="3eafa-113">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
