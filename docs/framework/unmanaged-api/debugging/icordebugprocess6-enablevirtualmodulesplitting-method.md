---
title: ICorDebugProcess6::EnableVirtualModuleSplitting 方法
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bd06dd3f58a1f74fbdb5ec61c4896f5c1696856
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931063"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting 方法
啟用或停用虛擬模組分割。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>參數  
 `enableSplitting`  
 若要啟用虛擬模組分割，則為 `true`；若要停用，則為 `false`。  
  
## <a name="remarks"></a>備註  
 虛擬模組分割可讓[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)辨識在組建程式期間合併在一起的模組, 並將其呈現為一組不同的模組, 而不是單一的大型模組。 這麼做會變更各種[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法的行為, 如下所述。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
 您可以呼叫這個方法並隨時變更 `enableSplitting` 的值。 除了改變[虛擬模組分割和未受管理的調試](#APIs)程式開發介面一節中所列的方法行為之外, 它不會在[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件中造成任何具狀態的功能變更。 呼叫這些方法時，使用虛擬模組確實會對效能帶來負面影響。 此外, 可能需要虛擬化中繼資料的大量記憶體內部快取, 才能正確地執行[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) api, 而且即使在關閉虛擬模組分割之後, 這些快取也可能會保留。  
  
## <a name="terminology"></a>用語  
 描述虛擬模組分割時會使用下列詞彙：  
  
 容器模組或容器  
 彙總模組。  
  
 子模組或虛擬模組  
 在容器中找到的模組。  
  
 一般模組  
 建置時間未合併的模組。 這些模組不是容器模組，就是子模組。  
  
 容器模組和子模組都會以 ICorDebugModule 介面物件來表示。 不過, 在每個案例中, 介面的行為會稍有不同, \<因為 > 一節中的 x 參考一節所述。  
  
## <a name="modules-and-assemblies"></a>模組和組件  
 組件合併案例不支援多模組組件，因此模組和組件之間有一對一關聯性。 無論每個 ICorDebugModule 物件是否代表容器模組或子模組, 都有對應的 ICorDebugAssembly 物件。 [ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法會將模組轉換成元件。 為了在另一個方向進行對應, [ICorDebugAssembly:: EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)方法只會列舉1個模組。 由於組件和模組在此情況下會形成緊密結合的配對，因此組件和模組兩個詞彙的互換情況會更高。  
  
## <a name="behavioral-differences"></a>行為的差異  
 容器模組具有下列行為和特性：  
  
- 所有構成子模組的中繼資料會合併在一起。  
  
- 其類型名稱可能會受損。  
  
- [ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法會傳回磁片上模組的路徑。  
  
- [ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法會傳回該影像的大小。  
  
- ICorDebugAssembly3.EnumerateContainedAssemblies 方法會列出子模組。  
  
- ICorDebugAssembly3.GetContainerAssembly 方法會傳回 `S_FALSE`。  
  
 子模組具有下列行為和特性：  
  
- 子模組包含一組縮減的中繼資料，只對應至已合併的原始組件。  
  
- 中繼資料名稱不會受損。  
  
- 中繼資料語彙基元不太可能符合原始組件在建置流程中合併前的語彙基元。  
  
- [ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法會傳回元件名稱, 而不是檔案路徑。  
  
- [ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法會傳回原始未合併的映射大小。  
  
- ICorDebugModule3.EnumerateContainedAssemblies 方法會傳回 `S_FALSE`。  
  
- ICorDebugAssembly3.GetContainerAssembly 方法會傳回所包含的模組。  
  
## <a name="interfaces-retrieved-from-modules"></a>從模組擷取的介面  
 可從模組建立或擷取的各種介面。 其中包括：  
  
- [ICorDebugModule:: GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)方法傳回的 ICorDebugClass 物件。  
  
- [ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法傳回的 ICorDebugAssembly 物件。  
  
 這些物件一律會由[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)快取, 而且不論是從容器模組或子模組建立或查詢, 它們都會有相同的指標識別。 子模組提供這些快取物件的篩選檢視，而不是其本身複本的個別快取。  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>虛擬模組分割和未受管理的偵錯 API  
 下表顯示虛擬模組分割如何影響未受管理之偵錯 API 中其他方法的行為。  
  
|方法|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|傳回這個函式原本定義所在的子模組|傳回已合併這個函式的目標容器模組|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|傳回這個類別原本定義所在的子模組|傳回已合併這個類別的目標容器模組。|  
|ICorDebugModuleDebugEvent::GetModule|傳回已載入的容器模組。 不論這個設定為何，都不會提供載入事件給子模組。|傳回已載入的容器模組。|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|傳回子組件和一般組件的清單，不包含任何容器組件。 **注意：** 如有任何容器組件遺漏符號，則不會列舉其子組件。 如有任何一般組件遺漏符號，則列舉或不列舉都有可能。|傳回容器組件和一般組件的清單，不包含任何子組件。 **注意：** 如有任何一般組件遺漏符號，則列舉或不列舉都有可能。|  
|[ICorDebugCode:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)(僅參考 IL 程式碼時)|傳回在預先合併組件映像中有效的 IL。 具體來說，當所參考的類型未在包含 IL 的虛擬模組中定義時，所有內嵌中繼資料語彙基元都會是正確的 TypeRef 或 MemberRef 語彙基元。 您可以在[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件中, 針對對應的虛擬 ICorDebugModule 物件查閱這些 TypeRef 或 MemberRef 標記。|傳回合併後組件映像中的 IL。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess6 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
