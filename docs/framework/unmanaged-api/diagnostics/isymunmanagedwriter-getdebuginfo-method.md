---
title: ISymUnmanagedWriter::GetDebugInfo 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: dcab63b603d4a9a8e1430228043d2a5e597bbf4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678288"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="ccc19-102">ISymUnmanagedWriter::GetDebugInfo 方法</span><span class="sxs-lookup"><span data-stu-id="ccc19-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>

<span data-ttu-id="ccc19-103">傳回編譯器在可攜式可執行檔 (PE) 檔標頭中寫入 debug directory 專案所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="ccc19-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="ccc19-104">符號寫入器會填入和以外的所有 `TimeDateStamp` 欄位 `PointerToRawData` 。</span><span class="sxs-lookup"><span data-stu-id="ccc19-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="ccc19-105"> (編譯器會負責適當地設定這兩個欄位。 ) </span><span class="sxs-lookup"><span data-stu-id="ccc19-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="ccc19-106">編譯器應該呼叫這個方法，將資料 blob 發出至 PE 檔案、將 `PointerToRawData` IMAGE_DEBUG_DIRECTORY 中的欄位設定為指向發出的資料，並將 IMAGE_DEBUG_DIRECTORY 寫入至 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="ccc19-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="ccc19-107">編譯器也應該將欄位設定 `TimeDateStamp` 為等於所 `TimeDateStamp` 產生之 PE 檔案的。</span><span class="sxs-lookup"><span data-stu-id="ccc19-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc19-108">語法</span><span class="sxs-lookup"><span data-stu-id="ccc19-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccc19-109">參數</span><span class="sxs-lookup"><span data-stu-id="ccc19-109">Parameters</span></span>  

 `pIDD`  
 <span data-ttu-id="ccc19-110">[in，out]符號寫入器將填寫的 IMAGE_DEBUG_DIRECTORY 指標。</span><span class="sxs-lookup"><span data-stu-id="ccc19-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="ccc19-111">在 `DWORD` ，包含偵錯工具資料的大小。</span><span class="sxs-lookup"><span data-stu-id="ccc19-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="ccc19-112">擴展的指標 `DWORD` ，會接收包含偵錯工具資料所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="ccc19-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="ccc19-113">擴展緩衝區的指標，此緩衝區夠大，足以容納符號存放區的偵錯工具資料。</span><span class="sxs-lookup"><span data-stu-id="ccc19-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccc19-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="ccc19-114">Return Value</span></span>  

 <span data-ttu-id="ccc19-115">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ccc19-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc19-116">需求</span><span class="sxs-lookup"><span data-stu-id="ccc19-116">Requirements</span></span>  

 <span data-ttu-id="ccc19-117">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ccc19-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc19-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccc19-118">See also</span></span>

- [<span data-ttu-id="ccc19-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="ccc19-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
