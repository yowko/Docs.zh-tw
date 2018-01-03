---
title: "ISymUnmanagedWriter::GetDebugInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f071bfe88397d6431fb50403c3969d82c5cfe8fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="d8fc3-102">ISymUnmanagedWriter::GetDebugInfo 方法</span><span class="sxs-lookup"><span data-stu-id="d8fc3-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="d8fc3-103">傳回編譯器在可攜式執行檔 (PE) 標頭寫入偵錯目錄項目所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="d8fc3-104">符號寫入器填寫所有欄位，除了`TimeDateStamp`和`PointerToRawData`。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="d8fc3-105">（編譯器會負責適當地設定這兩個欄位）。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="d8fc3-106">編譯器應該呼叫這個方法，發出資料 blob 的 PE 檔案，設定`PointerToRawData`指向發出的資料和 PE 檔寫入 IMAGE_DEBUG_DIRECTORY IMAGE_DEBUG_DIRECTORY 欄位。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="d8fc3-107">編譯器也應該設定`TimeDateStamp`欄位等於`TimeDateStamp`所產生的 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8fc3-108">語法</span><span class="sxs-lookup"><span data-stu-id="d8fc3-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8fc3-109">參數</span><span class="sxs-lookup"><span data-stu-id="d8fc3-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="d8fc3-110">[in、 out]符號寫入器，填妥 IMAGE_DEBUG_DIRECTORY 指標。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="d8fc3-111">[in]A`DWORD`包含偵錯資料的大小。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="d8fc3-112">[out]指標`DWORD`包含偵錯資料所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="d8fc3-113">[out]夠大，足以包含符號存放區的偵錯資料緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8fc3-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8fc3-114">Return Value</span></span>  
 <span data-ttu-id="d8fc3-115">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8fc3-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8fc3-116">需求</span><span class="sxs-lookup"><span data-stu-id="d8fc3-116">Requirements</span></span>  
 <span data-ttu-id="d8fc3-117">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d8fc3-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fc3-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8fc3-118">See Also</span></span>  
 [<span data-ttu-id="d8fc3-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d8fc3-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
