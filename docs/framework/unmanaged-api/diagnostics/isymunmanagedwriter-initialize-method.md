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
ms.openlocfilehash: c702aa32e8c8d6d5c137f7968d1578715102180f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726857"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="0b58b-102">ISymUnmanagedWriter::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="0b58b-102">ISymUnmanagedWriter::Initialize Method</span></span>

<span data-ttu-id="0b58b-103">設定與這個寫入器相關聯的中繼資料發射器介面，並設定將用來寫入偵錯工具符號的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="0b58b-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="0b58b-104">這個方法只能呼叫一次，而且必須在任何其他寫入器方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b58b-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="0b58b-105">有些寫入器可能需要檔案名。</span><span class="sxs-lookup"><span data-stu-id="0b58b-105">Some writers may require a file name.</span></span> <span data-ttu-id="0b58b-106">不過，您一律可以將檔案名傳遞給這個方法，而不會對不使用檔案名的寫入器產生任何負面影響。</span><span class="sxs-lookup"><span data-stu-id="0b58b-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b58b-107">語法</span><span class="sxs-lookup"><span data-stu-id="0b58b-107">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b58b-108">參數</span><span class="sxs-lookup"><span data-stu-id="0b58b-108">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="0b58b-109">在中繼資料的發射器介面指標。</span><span class="sxs-lookup"><span data-stu-id="0b58b-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="0b58b-110">在要寫入調試符號的檔案名。</span><span class="sxs-lookup"><span data-stu-id="0b58b-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="0b58b-111">如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="0b58b-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="0b58b-112">在如果有指定，符號寫入器會將符號發出至指定的， <xref:System.Runtime.InteropServices.ComTypes.IStream> 而不是在參數中指定的檔案 `filename` 。</span><span class="sxs-lookup"><span data-stu-id="0b58b-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="0b58b-113">`pIStream` 是選用參數。</span><span class="sxs-lookup"><span data-stu-id="0b58b-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="0b58b-114">[in] `true` 如果這是完整重建， `false` 如果這是累加式編譯，則為。</span><span class="sxs-lookup"><span data-stu-id="0b58b-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b58b-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="0b58b-115">Return Value</span></span>  

 <span data-ttu-id="0b58b-116">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0b58b-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b58b-117">需求</span><span class="sxs-lookup"><span data-stu-id="0b58b-117">Requirements</span></span>  

 <span data-ttu-id="0b58b-118">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0b58b-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b58b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b58b-119">See also</span></span>

- [<span data-ttu-id="0b58b-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="0b58b-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="0b58b-121">Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="0b58b-121">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)
