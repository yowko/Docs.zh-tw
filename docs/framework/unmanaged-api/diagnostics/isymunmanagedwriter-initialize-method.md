---
title: ISymUnmanagedWriter::Initialize 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1ea9424c000ad3ae4918181084c89038c2ec8d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777284"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="d1d7f-102">ISymUnmanagedWriter::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="d1d7f-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="d1d7f-103">設定與這個寫入器將會在相關的中繼資料發出器介面，並設定偵錯的符號寫入的輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="d1d7f-104">一次，呼叫這個方法，它必須在其他任何寫入方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="d1d7f-105">有些寫入器可能需要的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-105">Some writers may require a file name.</span></span> <span data-ttu-id="d1d7f-106">不過，您一律可以檔案名稱傳遞給這個方法沒有任何未使用的檔案名稱的寫入器上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d7f-107">語法</span><span class="sxs-lookup"><span data-stu-id="d1d7f-107">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d7f-108">參數</span><span class="sxs-lookup"><span data-stu-id="d1d7f-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="d1d7f-109">[in]中繼資料發出器介面指標。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="d1d7f-110">[in]寫入偵錯符號的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="d1d7f-111">如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="d1d7f-112">[in]如果指定，符號寫入器就會發出符號另外建立成給定<xref:System.Runtime.InteropServices.ComTypes.IStream>而不是在指定的檔案`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="d1d7f-113">`pIStream` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="d1d7f-114">[in]`true`如果這是完整重建，`false`如果這是累加編譯。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1d7f-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1d7f-115">Return Value</span></span>  
 <span data-ttu-id="d1d7f-116">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1d7f-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d7f-117">需求</span><span class="sxs-lookup"><span data-stu-id="d1d7f-117">Requirements</span></span>  
 <span data-ttu-id="d1d7f-118">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1d7f-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d7f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d7f-119">See also</span></span>

- [<span data-ttu-id="d1d7f-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d1d7f-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d1d7f-121">Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="d1d7f-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
