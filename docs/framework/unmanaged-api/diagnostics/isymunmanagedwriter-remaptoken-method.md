---
title: ISymUnmanagedWriter::RemapToken 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 8799815f7c6c6aefc7081f3583e6fd174cd478f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683553"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="30c3f-102">ISymUnmanagedWriter::RemapToken 方法</span><span class="sxs-lookup"><span data-stu-id="30c3f-102">ISymUnmanagedWriter::RemapToken Method</span></span>

<span data-ttu-id="30c3f-103">通知符號寫入器，元資料標記已在發出中繼資料時重新對應。</span><span class="sxs-lookup"><span data-stu-id="30c3f-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="30c3f-104">如果符號寫入器已將舊的權杖儲存在符號存放區中，則必須使用新值來更新儲存的權杖，或者必須儲存對應符號讀取器的對應，才能在讀取階段重新對應。</span><span class="sxs-lookup"><span data-stu-id="30c3f-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c3f-105">語法</span><span class="sxs-lookup"><span data-stu-id="30c3f-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30c3f-106">參數</span><span class="sxs-lookup"><span data-stu-id="30c3f-106">Parameters</span></span>  

 `oldToken`  
 <span data-ttu-id="30c3f-107">在重新對應的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="30c3f-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="30c3f-108">在重新對應的新元資料標記 `oldToken` 。</span><span class="sxs-lookup"><span data-stu-id="30c3f-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30c3f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="30c3f-109">Return Value</span></span>  

 <span data-ttu-id="30c3f-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="30c3f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c3f-111">需求</span><span class="sxs-lookup"><span data-stu-id="30c3f-111">Requirements</span></span>  

 <span data-ttu-id="30c3f-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="30c3f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c3f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30c3f-113">See also</span></span>

- [<span data-ttu-id="30c3f-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="30c3f-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
