---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 3ac8bb3a20ce82b734a572832a9cbb75fa2568c4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441899"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="8b7ac-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="8b7ac-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="8b7ac-103">取得特定檔中方法的最小起始行和最大結尾行。</span><span class="sxs-lookup"><span data-stu-id="8b7ac-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b7ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b7ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b7ac-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="8b7ac-106">在檔的指標。</span><span class="sxs-lookup"><span data-stu-id="8b7ac-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="8b7ac-107">脫銷`ULONG32`接收起始行之的指標。</span><span class="sxs-lookup"><span data-stu-id="8b7ac-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="8b7ac-108">脫銷`ULONG32`接收結束行之的指標。</span><span class="sxs-lookup"><span data-stu-id="8b7ac-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b7ac-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8b7ac-109">Return Value</span></span>  
 <span data-ttu-id="8b7ac-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8b7ac-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b7ac-111">需求</span><span class="sxs-lookup"><span data-stu-id="8b7ac-111">Requirements</span></span>  
 <span data-ttu-id="8b7ac-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8b7ac-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7ac-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b7ac-113">See also</span></span>

- [<span data-ttu-id="8b7ac-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="8b7ac-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
