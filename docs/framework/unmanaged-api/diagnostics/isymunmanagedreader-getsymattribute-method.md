---
title: ISymUnmanagedReader::GetSymAttribute 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: aa3b742babe4a94a43e4e6168dea67c0a0245eb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720577"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="98689-102">ISymUnmanagedReader::GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="98689-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>

<span data-ttu-id="98689-103">根據名稱，取得自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="98689-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="98689-104">與中繼資料自訂屬性不同的是，這些自訂屬性會保存在符號存放區中。</span><span class="sxs-lookup"><span data-stu-id="98689-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98689-105">語法</span><span class="sxs-lookup"><span data-stu-id="98689-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98689-106">參數</span><span class="sxs-lookup"><span data-stu-id="98689-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="98689-107">在要求屬性之物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="98689-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="98689-108">在變數的指標，指出要取出的屬性。</span><span class="sxs-lookup"><span data-stu-id="98689-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="98689-109">[in] `buffer` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="98689-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="98689-110">擴展變數的指標，此變數會接收屬性資料的長度。</span><span class="sxs-lookup"><span data-stu-id="98689-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="98689-111">擴展接收屬性資料之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="98689-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98689-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="98689-112">Return Value</span></span>  

 <span data-ttu-id="98689-113">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="98689-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98689-114">需求</span><span class="sxs-lookup"><span data-stu-id="98689-114">Requirements</span></span>  

 <span data-ttu-id="98689-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="98689-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98689-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98689-116">See also</span></span>

- [<span data-ttu-id="98689-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="98689-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
