---
title: IAssemblyEnum::GetNextAssembly 方法
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134442"
---
# <a name="iassemblyenumgetnextassembly-method"></a>IAssemblyEnum::GetNextAssembly 方法
取得包含在這個[IAssemblyEnum](iassemblyenum-interface.md)物件中的下一個[IAssemblyName](iassemblyname-interface.md)的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pvReserved`  
 在保留以供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
 `ppName`  
 脫銷傳回的 `IAssemblyName` 指標。  
  
 `dwFlags`  
 在保留以供未來擴充性之用。 `dwFlags` 必須是0（零）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [IAssemblyEnum 介面](iassemblyenum-interface.md)
