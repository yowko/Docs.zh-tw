---
title: "ISymUnmanagedWriter::GetDebugInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo 方法
傳回編譯器在可攜式執行檔 (PE) 標頭寫入偵錯目錄項目所需的資訊。 符號寫入器填寫所有欄位，除了`TimeDateStamp`和`PointerToRawData`。 （編譯器會負責適當地設定這兩個欄位）。  
  
 編譯器應該呼叫這個方法，發出資料 blob 的 PE 檔案，設定`PointerToRawData`指向發出的資料和 PE 檔寫入 IMAGE_DEBUG_DIRECTORY IMAGE_DEBUG_DIRECTORY 欄位。 編譯器也應該設定`TimeDateStamp`欄位等於`TimeDateStamp`所產生的 PE 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>參數  
 `pIDD`  
 [in、 out]符號寫入器，填妥 IMAGE_DEBUG_DIRECTORY 指標。  
  
 `cData`  
 [in]A`DWORD`包含偵錯資料的大小。  
  
 `pcData`  
 [out]指標`DWORD`包含偵錯資料所需的緩衝區大小。  
  
 `data`  
 [out]夠大，足以包含符號存放區的偵錯資料緩衝區的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
