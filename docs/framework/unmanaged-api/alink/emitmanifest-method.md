---
title: EmitManifest 方法
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: f3bb978b8358992fd9aa7da922e28efc1ed1a951
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446489"
---
# <a name="emitmanifest-method"></a>EmitManifest 方法
發出最後的資訊清單。 在匯入所有其他檔案並設定所有選項之後，請呼叫這個方法。 請勿針對未系結的模組呼叫此方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `AssemblyID`  
 元件的識別碼。  
  
 `pdwReserveSize`  
 接收要在元件檔中保留的大小，並從[StrongNameSignatureSize](../strong-naming/strongnamesignaturesize-function.md)函式中取出。  
  
 `ptkManifest`  
 選擇性地接收組件資訊清單 token。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
