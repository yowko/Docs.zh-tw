---
title: ICeeGen::GetSectionCreate 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 0cf7b15392c90694db659f6faff6feecbef65466
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008318"
---
# <a name="iceegengetsectioncreate-method"></a>ICeeGen::GetSectionCreate 方法
使用指定的名稱和旗標值，產生並取得程式碼區段。  
  
 這個方法已過時，不應使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 在字串的指標，指定要建立之區段的名稱。  
  
 `flags`  
 在指定選項的旗標。  
  
 `section`  
 脫銷新建立之程式碼區段的指標。  
  
## <a name="remarks"></a>備註  
 `GetSectionCreate`只有當您有其他方法未處理的特殊區段需求時，才需要呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICeeGen 介面](iceegen-interface.md)
