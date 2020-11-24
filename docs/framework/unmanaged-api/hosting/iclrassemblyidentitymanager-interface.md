---
title: ICLRAssemblyIdentityManager 介面
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: 41d049c931091d2cc0b41bd1e9d74b3c15d7878d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679256"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager 介面

提供方法，可支援主機和 common language runtime 之間的通訊， (CLR) 有關元件的資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBindingIdentityFromFile 方法](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|取得位於指定檔案路徑之元件的元件識別系結資料。|  
|[GetBindingIdentityFromStream 方法](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|取得指定之資料流程中元件的標準元件身分識別資料。|  
|[GetCLRAssemblyReferenceList 方法](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|從提供的部分元件身分識別清單取得 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 實例。|  
|[GetProbingAssembliesFromReference 方法](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|取得元件的 [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列舉值，該元件是由具有指定身分識別的元件所參考。|  
|[GetReferencedAssembliesFromFile 方法](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|取得 [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) 實例，其中包含元件在指定檔案路徑所參考的元件清單。|  
|[GetReferencedAssembliesFromStream 方法](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|取得 `ICLRReferenceAssemblyEnum` 物件的指標，該物件包含指定資料流程中元件所參考之元件的元件身分識別資料。|  
|[IsStronglyNamed 方法](iclrassemblyidentitymanager-isstronglynamed-method.md)|取得值，這個值會指出指定的元件是否為強式名稱。|  
  
## <a name="remarks"></a>備註  

 使用 `ICLRAssemblyIdentityManager` 取得的實例 `ICLRAssemblyReferenceList` 和，以列舉元件身分識別。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum 介面](iclrprobingassemblyenum-interface.md)
- [裝載介面](hosting-interfaces.md)
