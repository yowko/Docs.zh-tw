---
title: ICorDebugSymbolProvider2::GetFrameProps 方法
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: dc64152938c46945978715251286ecb6c6d8983c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791515"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2::GetFrameProps 方法
傳回某方法啟動相關的虛擬位址，以及被指定程式碼相關的虛擬位址的之父框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>參數  
 `codeRva`  
 [in] 與程式碼相關的虛擬位址。  
  
 `pCodeStartRva`  
 [out] 指向該方法的啟動相關虛擬位址之指標。  
  
 `pParentFrameStartRva`  
 [out] 指向該框架的啟動相關虛擬位址之指標。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugSymbolProvider2 介面](icordebugsymbolprovider2-interface.md)
- [偵錯介面](debugging-interfaces.md)
