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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 979d14b4c404c3bf12c427bd5b8b1d4997805e7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986007"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="6c37a-102">ISymUnmanagedWriter::RemapToken 方法</span><span class="sxs-lookup"><span data-stu-id="6c37a-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="6c37a-103">通知的符號寫入器中繼資料語彙基元已重新對應，因為在發出中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6c37a-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="6c37a-104">如果符號寫入器已存放在符號存放區中舊的語彙基元，則它必須的更新為新的值，或者使用儲存的權杖必須儲存對應的符號讀取器在讀取階段期間重新對應的對應。</span><span class="sxs-lookup"><span data-stu-id="6c37a-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c37a-105">語法</span><span class="sxs-lookup"><span data-stu-id="6c37a-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c37a-106">參數</span><span class="sxs-lookup"><span data-stu-id="6c37a-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="6c37a-107">[in]已重新對應中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6c37a-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="6c37a-108">[in]新的中繼資料語彙基元的`oldToken`已重新對應。</span><span class="sxs-lookup"><span data-stu-id="6c37a-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c37a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c37a-109">Return Value</span></span>  
 <span data-ttu-id="6c37a-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c37a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c37a-111">需求</span><span class="sxs-lookup"><span data-stu-id="6c37a-111">Requirements</span></span>  
 <span data-ttu-id="6c37a-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c37a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c37a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c37a-113">See also</span></span>

- [<span data-ttu-id="6c37a-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="6c37a-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
