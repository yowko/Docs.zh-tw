---
title: ISymUnmanagedMethod::GetSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 38763e687c66dcb038a874c9c17cb0d67e547816
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699348"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="7b691-102">ISymUnmanagedMethod::GetSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="7b691-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>

<span data-ttu-id="7b691-103">取得此方法內的所有序列點。</span><span class="sxs-lookup"><span data-stu-id="7b691-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b691-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b691-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b691-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b691-105">Parameters</span></span>  

 `cPoints`  
 <span data-ttu-id="7b691-106">在， `ULONG32` 接收 `offsets` 、 `documents` 、 `lines` 、、 `columns` `endLines` 和 `endColumns` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="7b691-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="7b691-107">擴展的指標 `ULONG32` ，會接收包含序列點所需的緩衝區長度。</span><span class="sxs-lookup"><span data-stu-id="7b691-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="7b691-108">在要在其中儲存 Microsoft 中繼語言 (MSIL 的陣列，) 序列點之方法開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="7b691-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="7b691-109">在要在其中儲存序列點所在檔的陣列。</span><span class="sxs-lookup"><span data-stu-id="7b691-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="7b691-110">在陣列，要在其中儲存序列點所在檔中的行。</span><span class="sxs-lookup"><span data-stu-id="7b691-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="7b691-111">在陣列，要在其中儲存序列點所在檔中的資料行。</span><span class="sxs-lookup"><span data-stu-id="7b691-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="7b691-112">在順序點結束之檔中的行陣列。</span><span class="sxs-lookup"><span data-stu-id="7b691-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="7b691-113">在順序點結束之檔中的資料行陣列。</span><span class="sxs-lookup"><span data-stu-id="7b691-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b691-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b691-114">Return Value</span></span>  

 <span data-ttu-id="7b691-115">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7b691-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b691-116">需求</span><span class="sxs-lookup"><span data-stu-id="7b691-116">Requirements</span></span>  

 <span data-ttu-id="7b691-117">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="7b691-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b691-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b691-118">See also</span></span>

- [<span data-ttu-id="7b691-119">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="7b691-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
