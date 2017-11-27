---
title: "ISymUnmanagedWriter::Initialize2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e76543c35a717b95ae37985648986abaf16bf85d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="e59d3-102">ISymUnmanagedWriter::Initialize2 方法</span><span class="sxs-lookup"><span data-stu-id="e59d3-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="e59d3-103">設定與這個寫入器將會在相關的中繼資料發出器介面，並將偵錯符號寫入的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="e59d3-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="e59d3-104">這個方法也可讓您設定的程式資料庫 (PDB) 檔案的最終位置。</span><span class="sxs-lookup"><span data-stu-id="e59d3-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e59d3-105">語法</span><span class="sxs-lookup"><span data-stu-id="e59d3-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e59d3-106">參數</span><span class="sxs-lookup"><span data-stu-id="e59d3-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="e59d3-107">[in]中繼資料發出器介面指標。</span><span class="sxs-lookup"><span data-stu-id="e59d3-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="e59d3-108">[in]指標`WCHAR`包含偵錯符號寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e59d3-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="e59d3-109">如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。</span><span class="sxs-lookup"><span data-stu-id="e59d3-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="e59d3-110">[in]如果指定，符號寫入器發出符號插入給定<xref:System.Runtime.InteropServices.ComTypes.IStream>，而不是檔案中指定`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="e59d3-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="e59d3-111">`pIStream` 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="e59d3-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="e59d3-112">[in]`true`如果這是完整重建;`false`如果這是累加編譯。</span><span class="sxs-lookup"><span data-stu-id="e59d3-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="e59d3-113">[in]指標`WCHAR`也就是在 PDB 檔案的最終位置的路徑字串。</span><span class="sxs-lookup"><span data-stu-id="e59d3-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e59d3-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="e59d3-114">Return Value</span></span>  
 <span data-ttu-id="e59d3-115">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e59d3-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e59d3-116">需求</span><span class="sxs-lookup"><span data-stu-id="e59d3-116">Requirements</span></span>  
 <span data-ttu-id="e59d3-117">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e59d3-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e59d3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e59d3-118">See Also</span></span>  
 [<span data-ttu-id="e59d3-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="e59d3-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="e59d3-120">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="e59d3-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
