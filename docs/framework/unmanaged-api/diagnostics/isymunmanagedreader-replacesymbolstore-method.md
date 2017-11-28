---
title: "ISymUnmanagedReader::ReplaceSymbolStore 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.ReplaceSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09bcad4898cf4d3310a96164bdc82006e185006f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="32718-102">ISymUnmanagedReader::ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="32718-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="32718-103">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="32718-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="32718-104">這個方法是類似於[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法，不同之處在於指定的差異做為完全取代，而非更新。</span><span class="sxs-lookup"><span data-stu-id="32718-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32718-105">您必須指定其中`filename`或`pIStream`參數不可同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="32718-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="32718-106">如果`filename`指定，則使用該檔案中的符號，符號存放區將會更新。</span><span class="sxs-lookup"><span data-stu-id="32718-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="32718-107">如果`pIStream`指定，則會更新存放區，以從資料<xref:System.Runtime.InteropServices.ComTypes.IStream>。</span><span class="sxs-lookup"><span data-stu-id="32718-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32718-108">語法</span><span class="sxs-lookup"><span data-stu-id="32718-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32718-109">參數</span><span class="sxs-lookup"><span data-stu-id="32718-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="32718-110">[in]包含符號存放區的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="32718-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="32718-111">[in]檔案資料流，做為替代`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="32718-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32718-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="32718-112">Return Value</span></span>  
 <span data-ttu-id="32718-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="32718-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32718-114">需求</span><span class="sxs-lookup"><span data-stu-id="32718-114">Requirements</span></span>  
 <span data-ttu-id="32718-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32718-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32718-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32718-116">See Also</span></span>  
 [<span data-ttu-id="32718-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="32718-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
