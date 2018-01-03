---
title: "ISymUnmanagedReader::UpdateSymbolStore 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.UpdateSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 267037cbdf9e9bf45454bd8b584563ba1ecd847d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="973c3-102">ISymUnmanagedReader::UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="973c3-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="973c3-103">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="973c3-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="973c3-104">這個方法用於在編輯後繼續的情況下更新符號存放區，以符合原始可攜式執行檔 (PE) 的差異。</span><span class="sxs-lookup"><span data-stu-id="973c3-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="973c3-105">您必須指定其中`filename`或`pIStream`參數不可同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="973c3-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="973c3-106">如果`filename`指定，則使用該檔案中的符號，符號存放區將會更新。</span><span class="sxs-lookup"><span data-stu-id="973c3-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="973c3-107">如果`pIStream`指定，則會更新存放區，以從資料<xref:System.Runtime.InteropServices.ComTypes.IStream>。</span><span class="sxs-lookup"><span data-stu-id="973c3-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="973c3-108">語法</span><span class="sxs-lookup"><span data-stu-id="973c3-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="973c3-109">參數</span><span class="sxs-lookup"><span data-stu-id="973c3-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="973c3-110">[in]包含符號存放區的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="973c3-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="973c3-111">[in]檔案資料流，做為替代`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="973c3-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="973c3-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="973c3-112">Return Value</span></span>  
 <span data-ttu-id="973c3-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="973c3-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="973c3-114">需求</span><span class="sxs-lookup"><span data-stu-id="973c3-114">Requirements</span></span>  
 <span data-ttu-id="973c3-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="973c3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="973c3-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="973c3-116">See Also</span></span>  
 [<span data-ttu-id="973c3-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="973c3-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
