---
title: "ISymUnmanagedWriter::Initialize 方法"
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
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 737e6b5218d51d8a1a051104ecdd11240a2ddac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="a57f9-102">ISymUnmanagedWriter::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="a57f9-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="a57f9-103">設定與這個寫入器將會在相關的中繼資料發出器介面，並將偵錯符號寫入的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="a57f9-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="a57f9-104">一次，呼叫這個方法，它必須進行任何其他寫入器方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="a57f9-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="a57f9-105">有些寫入器可能需要的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a57f9-105">Some writers may require a file name.</span></span> <span data-ttu-id="a57f9-106">不過，您一律可以檔案名稱傳遞至這個方法沒有任何未使用的檔案名稱的寫入器上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="a57f9-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a57f9-107">語法</span><span class="sxs-lookup"><span data-stu-id="a57f9-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a57f9-108">參數</span><span class="sxs-lookup"><span data-stu-id="a57f9-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="a57f9-109">[in]中繼資料發出器介面指標。</span><span class="sxs-lookup"><span data-stu-id="a57f9-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="a57f9-110">[in]偵錯符號寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a57f9-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="a57f9-111">如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a57f9-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="a57f9-112">[in]如果指定，符號寫入器會發出符號插入給定<xref:System.Runtime.InteropServices.ComTypes.IStream>，而不是檔案中指定`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="a57f9-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="a57f9-113">`pIStream` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="a57f9-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="a57f9-114">[in]`true`如果這是完整重建;`false`如果這是累加編譯。</span><span class="sxs-lookup"><span data-stu-id="a57f9-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a57f9-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="a57f9-115">Return Value</span></span>  
 <span data-ttu-id="a57f9-116">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a57f9-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a57f9-117">需求</span><span class="sxs-lookup"><span data-stu-id="a57f9-117">Requirements</span></span>  
 <span data-ttu-id="a57f9-118">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a57f9-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57f9-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a57f9-119">See Also</span></span>  
 [<span data-ttu-id="a57f9-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a57f9-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="a57f9-121">Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="a57f9-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
