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
ms.openlocfilehash: f8eb4cb6bad95295e10a72812fa8dbb0adfcc898
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614782"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo 方法
傳回編譯器在可移植執行檔（PE）檔案標頭中寫入 debug 目錄專案所需的資訊。 符號寫入器會填滿除了和以外的所有欄位 `TimeDateStamp` `PointerToRawData` 。 （編譯器會負責適當地設定這兩個欄位）。  
  
 編譯器應該呼叫這個方法，將資料 blob 發出至 PE 檔案，將 `PointerToRawData` IMAGE_DEBUG_DIRECTORY 中的欄位設定為指向發出的資料，並將 IMAGE_DEBUG_DIRECTORY 寫入 pe 檔案。 編譯器也應該將欄位設定 `TimeDateStamp` 為等於所 `TimeDateStamp` 產生之 PE 檔案的。  
  
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
 [in、out]符號寫入器將填入之 IMAGE_DEBUG_DIRECTORY 的指標。  
  
 `cData`  
 在`DWORD`，包含偵錯工具資料的大小。  
  
 `pcData`  
 脫銷的指標 `DWORD` ，接收包含偵錯工具資料所需的緩衝區大小。  
  
 `data`  
 脫銷緩衝區的指標，夠大，足以容納符號存放區的 debug 資料。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
