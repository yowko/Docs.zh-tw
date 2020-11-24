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
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo 方法

傳回編譯器在可攜式可執行檔 (PE) 檔標頭中寫入 debug directory 專案所需的資訊。 符號寫入器會填入和以外的所有 `TimeDateStamp` 欄位 `PointerToRawData` 。  (編譯器會負責適當地設定這兩個欄位。 )   
  
 編譯器應該呼叫這個方法，將資料 blob 發出至 PE 檔案、將 `PointerToRawData` IMAGE_DEBUG_DIRECTORY 中的欄位設定為指向發出的資料，並將 IMAGE_DEBUG_DIRECTORY 寫入至 PE 檔。 編譯器也應該將欄位設定 `TimeDateStamp` 為等於所 `TimeDateStamp` 產生之 PE 檔案的。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>參數  

 `pIDD`  
 [in，out]符號寫入器將填寫的 IMAGE_DEBUG_DIRECTORY 指標。  
  
 `cData`  
 在 `DWORD` ，包含偵錯工具資料的大小。  
  
 `pcData`  
 擴展的指標 `DWORD` ，會接收包含偵錯工具資料所需的緩衝區大小。  
  
 `data`  
 擴展緩衝區的指標，此緩衝區夠大，足以容納符號存放區的偵錯工具資料。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
