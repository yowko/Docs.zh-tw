---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: b12ecfdaf7c90589ce2e96b39f7437444cb91b09
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615419"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="37dcf-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="37dcf-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="37dcf-103">取得符號讀取器方法，並指定方法權杖和編輯後繼續版本號碼。</span><span class="sxs-lookup"><span data-stu-id="37dcf-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="37dcf-104">版本號碼從1開始，每次方法因編輯後繼續作業而變更時，都會遞增。</span><span class="sxs-lookup"><span data-stu-id="37dcf-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37dcf-105">語法</span><span class="sxs-lookup"><span data-stu-id="37dcf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37dcf-106">參數</span><span class="sxs-lookup"><span data-stu-id="37dcf-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="37dcf-107">在方法元資料標記。</span><span class="sxs-lookup"><span data-stu-id="37dcf-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="37dcf-108">在方法版本。</span><span class="sxs-lookup"><span data-stu-id="37dcf-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="37dcf-109">脫銷傳回之[ISymUnmanagedMethod](isymunmanagedmethod-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="37dcf-109">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37dcf-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="37dcf-110">Return Value</span></span>  
 <span data-ttu-id="37dcf-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="37dcf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37dcf-112">需求</span><span class="sxs-lookup"><span data-stu-id="37dcf-112">Requirements</span></span>  
 <span data-ttu-id="37dcf-113">**標頭：** CorSym .idl。</span><span class="sxs-lookup"><span data-stu-id="37dcf-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="37dcf-114">CorSym。h</span><span class="sxs-lookup"><span data-stu-id="37dcf-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37dcf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37dcf-115">See also</span></span>

- [<span data-ttu-id="37dcf-116">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="37dcf-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
