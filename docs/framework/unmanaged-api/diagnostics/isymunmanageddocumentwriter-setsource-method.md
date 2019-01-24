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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da19a77637e64fec676fdaac7ba56d47b5b07769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549885"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="aca0c-102">ISymUnmanagedDocumentWriter::SetSource 方法</span><span class="sxs-lookup"><span data-stu-id="aca0c-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="aca0c-103">設定內嵌正在寫入的文件的來源。</span><span class="sxs-lookup"><span data-stu-id="aca0c-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="aca0c-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="aca0c-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="aca0c-106">[in]A `ULONG32` ，其中包含大小`source`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="aca0c-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="aca0c-107">[in]儲存內嵌的來源緩衝區。</span><span class="sxs-lookup"><span data-stu-id="aca0c-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aca0c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="aca0c-108">Return Value</span></span>  
 <span data-ttu-id="aca0c-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="aca0c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca0c-110">需求</span><span class="sxs-lookup"><span data-stu-id="aca0c-110">Requirements</span></span>  
 <span data-ttu-id="aca0c-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aca0c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca0c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aca0c-112">See also</span></span>
- [<span data-ttu-id="aca0c-113">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="aca0c-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
