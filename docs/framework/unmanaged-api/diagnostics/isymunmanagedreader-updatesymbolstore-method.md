---
title: ISymUnmanagedReader::UpdateSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938998"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="9adc8-102">ISymUnmanagedReader::UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="9adc8-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="9adc8-103">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="9adc8-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="9adc8-104">這個方法是在編輯後繼續案例中使用, 以更新符號存放區, 以符合原始可移植執行檔 (PE) 檔案的差異。</span><span class="sxs-lookup"><span data-stu-id="9adc8-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9adc8-105">您只需要指定其中一個`filename`或`pIStream`參數, 而不是兩者。</span><span class="sxs-lookup"><span data-stu-id="9adc8-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="9adc8-106">如果`filename`指定了, 符號存放區將會以該檔案中的符號進行更新。</span><span class="sxs-lookup"><span data-stu-id="9adc8-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="9adc8-107">如果`pIStream`指定了, 則會使用<xref:System.Runtime.InteropServices.ComTypes.IStream>中的資料來更新存放區。</span><span class="sxs-lookup"><span data-stu-id="9adc8-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9adc8-108">語法</span><span class="sxs-lookup"><span data-stu-id="9adc8-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9adc8-109">參數</span><span class="sxs-lookup"><span data-stu-id="9adc8-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="9adc8-110">在包含符號存放區的檔案名。</span><span class="sxs-lookup"><span data-stu-id="9adc8-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="9adc8-111">在檔案資料流程, 用來`filename`做為參數的替代方法。</span><span class="sxs-lookup"><span data-stu-id="9adc8-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9adc8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="9adc8-112">Return Value</span></span>  
 <span data-ttu-id="9adc8-113">如果方法成功, 則為 S_OK;否則, E_FAIL 或其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9adc8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9adc8-114">需求</span><span class="sxs-lookup"><span data-stu-id="9adc8-114">Requirements</span></span>  
 <span data-ttu-id="9adc8-115">**標頭：** CorSym .idl, CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9adc8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9adc8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9adc8-116">See also</span></span>

- [<span data-ttu-id="9adc8-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="9adc8-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
