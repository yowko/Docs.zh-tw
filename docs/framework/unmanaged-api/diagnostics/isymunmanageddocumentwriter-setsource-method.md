---
title: "ISymUnmanagedDocumentWriter::SetSource 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 287eba260ca20bae9da94ed2d00dcf1661fe14cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="6b400-102">ISymUnmanagedDocumentWriter::SetSource 方法</span><span class="sxs-lookup"><span data-stu-id="6b400-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="6b400-103">設定內嵌正在寫入的文件的來源。</span><span class="sxs-lookup"><span data-stu-id="6b400-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b400-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b400-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b400-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b400-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="6b400-106">[in]A`ULONG32`包含大小`source`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6b400-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="6b400-107">[in]儲存內嵌的來源緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6b400-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b400-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b400-108">Return Value</span></span>  
 <span data-ttu-id="6b400-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="6b400-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b400-110">需求</span><span class="sxs-lookup"><span data-stu-id="6b400-110">Requirements</span></span>  
 <span data-ttu-id="6b400-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6b400-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b400-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b400-112">See Also</span></span>  
 [<span data-ttu-id="6b400-113">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="6b400-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
