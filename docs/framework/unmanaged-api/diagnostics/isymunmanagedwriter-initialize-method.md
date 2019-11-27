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
ms.openlocfilehash: 6e9ab623d5fe9fcfda2305df078e988a561afdc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427970"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="bbe78-102">ISymUnmanagedWriter::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="bbe78-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="bbe78-103">設定此寫入器將與之關聯的中繼資料發射器介面，並設定要寫入偵錯工具符號的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="bbe78-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="bbe78-104">這個方法只能呼叫一次，而且必須在任何其他寫入器方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="bbe78-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="bbe78-105">某些寫入器可能需要檔案名。</span><span class="sxs-lookup"><span data-stu-id="bbe78-105">Some writers may require a file name.</span></span> <span data-ttu-id="bbe78-106">不過，您一律可以將檔案名傳遞給這個方法，而不會對不使用檔案名的寫入器產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="bbe78-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe78-107">語法</span><span class="sxs-lookup"><span data-stu-id="bbe78-107">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbe78-108">參數</span><span class="sxs-lookup"><span data-stu-id="bbe78-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="bbe78-109">在中繼資料發射器介面的指標。</span><span class="sxs-lookup"><span data-stu-id="bbe78-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="bbe78-110">在要在其中寫入調試符號的檔案名。</span><span class="sxs-lookup"><span data-stu-id="bbe78-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="bbe78-111">如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="bbe78-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="bbe78-112">在如果指定，符號寫入器會將符號發出至指定的 <xref:System.Runtime.InteropServices.ComTypes.IStream>，而不是 `filename` 參數中指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="bbe78-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="bbe78-113">`pIStream` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="bbe78-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="bbe78-114">[in] `true` 如果這是完整重建，則為，如果這是累加式編譯，`false`。</span><span class="sxs-lookup"><span data-stu-id="bbe78-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbe78-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="bbe78-115">Return Value</span></span>  
 <span data-ttu-id="bbe78-116">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bbe78-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe78-117">需求</span><span class="sxs-lookup"><span data-stu-id="bbe78-117">Requirements</span></span>  
 <span data-ttu-id="bbe78-118">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bbe78-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe78-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbe78-119">See also</span></span>

- [<span data-ttu-id="bbe78-120">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bbe78-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="bbe78-121">Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="bbe78-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
