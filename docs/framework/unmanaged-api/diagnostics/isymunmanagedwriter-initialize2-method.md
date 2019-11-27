---
title: ISymUnmanagedWriter::Initialize2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427953"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="a8b87-102">ISymUnmanagedWriter::Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="a8b87-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="a8b87-103">設定此寫入器將與之關聯的中繼資料發射器介面，並設定要寫入偵錯工具符號的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="a8b87-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="a8b87-104">此方法也可讓您設定程式資料庫（PDB）檔案的最終位置。</span><span class="sxs-lookup"><span data-stu-id="a8b87-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8b87-105">語法</span><span class="sxs-lookup"><span data-stu-id="a8b87-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8b87-106">參數</span><span class="sxs-lookup"><span data-stu-id="a8b87-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="a8b87-107">在中繼資料發射器介面的指標。</span><span class="sxs-lookup"><span data-stu-id="a8b87-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="a8b87-108">在`WCHAR` 的指標，其中包含要對其寫入偵錯工具符號的檔案名。</span><span class="sxs-lookup"><span data-stu-id="a8b87-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="a8b87-109">如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a8b87-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="a8b87-110">在如果指定，符號寫入器會將符號發出至指定的 <xref:System.Runtime.InteropServices.ComTypes.IStream>，而不是 `filename` 參數中指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b87-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="a8b87-111">`pIStream` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="a8b87-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="a8b87-112">[in] `true` 如果這是完整重建，則為，如果這是累加式編譯，`false`。</span><span class="sxs-lookup"><span data-stu-id="a8b87-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="a8b87-113">在`WCHAR` 的指標，這是 PDB 檔案最後位置的路徑字串。</span><span class="sxs-lookup"><span data-stu-id="a8b87-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8b87-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="a8b87-114">Return Value</span></span>  
 <span data-ttu-id="a8b87-115">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a8b87-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8b87-116">需求</span><span class="sxs-lookup"><span data-stu-id="a8b87-116">Requirements</span></span>  
 <span data-ttu-id="a8b87-117">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a8b87-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b87-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b87-118">See also</span></span>

- [<span data-ttu-id="a8b87-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a8b87-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a8b87-120">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="a8b87-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
