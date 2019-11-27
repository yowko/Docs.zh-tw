---
title: ISymUnmanagedMethod::GetSourceStartEnd 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 01ab69b73a7bc4929e2ebd49b3847f8d7c4646a2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448859"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="7333a-102">ISymUnmanagedMethod::GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="7333a-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="7333a-103">取得這個方法之來源的開始和結束檔位置。</span><span class="sxs-lookup"><span data-stu-id="7333a-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="7333a-104">第一個陣列位置是 start，而第二個數組位置是結尾。</span><span class="sxs-lookup"><span data-stu-id="7333a-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7333a-105">語法</span><span class="sxs-lookup"><span data-stu-id="7333a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7333a-106">參數</span><span class="sxs-lookup"><span data-stu-id="7333a-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="7333a-107">在開始和結束的來源文件。</span><span class="sxs-lookup"><span data-stu-id="7333a-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="7333a-108">在對應來源文件中的開始和結束行。</span><span class="sxs-lookup"><span data-stu-id="7333a-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="7333a-109">在對應來源文件中的開始和結束資料行。</span><span class="sxs-lookup"><span data-stu-id="7333a-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="7333a-110">[out] `true` 如果已定義位置，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="7333a-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7333a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7333a-111">Return Value</span></span>  
 <span data-ttu-id="7333a-112">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7333a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7333a-113">需求</span><span class="sxs-lookup"><span data-stu-id="7333a-113">Requirements</span></span>  
 <span data-ttu-id="7333a-114">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="7333a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7333a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="7333a-115">See also</span></span>

- [<span data-ttu-id="7333a-116">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="7333a-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
