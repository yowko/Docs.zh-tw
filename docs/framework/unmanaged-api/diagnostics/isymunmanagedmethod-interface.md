---
title: ISymUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: b72a77fecd15a43efbddd9dfd4618897c3372f88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699270"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="d45de-102">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="d45de-102">ISymUnmanagedMethod Interface</span></span>

<span data-ttu-id="d45de-103">代表符號存放區內的方法。</span><span class="sxs-lookup"><span data-stu-id="d45de-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="d45de-104">這個介面僅提供方法的符號相關屬性的存取權，而不是與型別相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="d45de-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d45de-105">方法</span><span class="sxs-lookup"><span data-stu-id="d45de-105">Methods</span></span>  
  
|<span data-ttu-id="d45de-106">方法</span><span class="sxs-lookup"><span data-stu-id="d45de-106">Method</span></span>|<span data-ttu-id="d45de-107">描述</span><span class="sxs-lookup"><span data-stu-id="d45de-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d45de-108">GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="d45de-109">取得在其中定義此方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d45de-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="d45de-110">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="d45de-111">傳回這個方法中，對應至檔內指定位置的位移。</span><span class="sxs-lookup"><span data-stu-id="d45de-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="d45de-112">GetParameters 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="d45de-113">取得這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="d45de-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="d45de-114">GetRanges 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="d45de-115">在檔中指定位置時，會傳回一組開始和結束位移組的陣列，其對應至該位置在此方法內所涵蓋的 Microsoft 中繼語言 (MSIL) 範圍。</span><span class="sxs-lookup"><span data-stu-id="d45de-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="d45de-116">GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="d45de-117">取得此方法內的根詞彙範圍。</span><span class="sxs-lookup"><span data-stu-id="d45de-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="d45de-118">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="d45de-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="d45de-119">GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="d45de-120">取得這個方法內的最封閉詞彙範圍，該範圍會括住指定的位移。</span><span class="sxs-lookup"><span data-stu-id="d45de-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="d45de-121">GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="d45de-122">取得此方法內的序列點計數。</span><span class="sxs-lookup"><span data-stu-id="d45de-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="d45de-123">GetSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="d45de-124">取得此方法內的所有序列點。</span><span class="sxs-lookup"><span data-stu-id="d45de-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="d45de-125">GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="d45de-126">取得此方法之來源的開始和結束檔位置。</span><span class="sxs-lookup"><span data-stu-id="d45de-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="d45de-127">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="d45de-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="d45de-128">傳回這個方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d45de-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d45de-129">需求</span><span class="sxs-lookup"><span data-stu-id="d45de-129">Requirements</span></span>  

 <span data-ttu-id="d45de-130">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d45de-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45de-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d45de-131">See also</span></span>

- [<span data-ttu-id="d45de-132">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d45de-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
