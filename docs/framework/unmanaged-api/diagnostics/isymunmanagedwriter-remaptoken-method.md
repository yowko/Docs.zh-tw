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
ms.openlocfilehash: 53cc908e0dc8cc5cc980ec365ccac0df4e620cac
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609764"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="a0c5e-102">ISymUnmanagedWriter::RemapToken 方法</span><span class="sxs-lookup"><span data-stu-id="a0c5e-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="a0c5e-103">通知符號寫入器，元資料標記在發出中繼資料時已重新對應。</span><span class="sxs-lookup"><span data-stu-id="a0c5e-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="a0c5e-104">如果符號寫入器已在符號存放區中儲存舊的 token，則必須使用新的值來更新儲存的 token，或在讀取階段期間，必須儲存對應符號讀取器的對應。</span><span class="sxs-lookup"><span data-stu-id="a0c5e-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c5e-105">語法</span><span class="sxs-lookup"><span data-stu-id="a0c5e-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0c5e-106">參數</span><span class="sxs-lookup"><span data-stu-id="a0c5e-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="a0c5e-107">在重新對應的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="a0c5e-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="a0c5e-108">在重新對應的新元資料標記 `oldToken` 。</span><span class="sxs-lookup"><span data-stu-id="a0c5e-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0c5e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a0c5e-109">Return Value</span></span>  
 <span data-ttu-id="a0c5e-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a0c5e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c5e-111">需求</span><span class="sxs-lookup"><span data-stu-id="a0c5e-111">Requirements</span></span>  
 <span data-ttu-id="a0c5e-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a0c5e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c5e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c5e-113">See also</span></span>

- [<span data-ttu-id="a0c5e-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a0c5e-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
