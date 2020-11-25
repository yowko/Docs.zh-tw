---
title: ISymUnmanagedReader2::GetSymAttributePreRemap 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 812c0d08930efff9140c6e897d3f93c4909e8464
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709085"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="6b572-102">ISymUnmanagedReader2::GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="6b572-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>

<span data-ttu-id="6b572-103">根據名稱，取得自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="6b572-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="6b572-104">不同于中繼資料自訂屬性，這些屬性會保存在符號存放區中。</span><span class="sxs-lookup"><span data-stu-id="6b572-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b572-105">語法</span><span class="sxs-lookup"><span data-stu-id="6b572-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b572-106">參數</span><span class="sxs-lookup"><span data-stu-id="6b572-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="6b572-107">在父系的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="6b572-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="6b572-108">在包含名稱之的指標 `WCHAR` 。</span><span class="sxs-lookup"><span data-stu-id="6b572-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="6b572-109">在 `ULONG32` ，指出陣列的大小 `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="6b572-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="6b572-110">擴展的指標 `ULONG32` ，會接收包含屬性位元組所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="6b572-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="6b572-111">擴展接收屬性位元組之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="6b572-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b572-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b572-112">Return Value</span></span>  

 <span data-ttu-id="6b572-113">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6b572-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b572-114">需求</span><span class="sxs-lookup"><span data-stu-id="6b572-114">Requirements</span></span>  

 <span data-ttu-id="6b572-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6b572-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b572-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b572-116">See also</span></span>

- [<span data-ttu-id="6b572-117">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="6b572-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
