---
title: ICorDebugProcess6::EnableVirtualModuleSplitting 方法
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15269646e967d3b260b305db5999a7b5e63be33b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736431"
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
 虛擬模組分割可讓[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)辨識處理在建置期間合併在一起的模組，並呈現以一組個別的模組，而不是以單一大型模組。 執行此動作會變更行為的各種[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)如下所述的方法。  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
 您可以呼叫這個方法並隨時變更 `enableSplitting` 的值。 它不會造成任何具狀態的功能性變更，在[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)改變行為中所列的方法以外的物件[虛擬模組分割和未受管理的偵錯 Api](#APIs)在這些呼叫的區段。 呼叫這些方法時，使用虛擬模組確實會對效能帶來負面影響。 此外，大量記憶體中快取的虛擬化的中繼資料可能需要正確地實作[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)可能保留的 Api，而且這些快取，即使虛擬模組分割已關閉。  
  
## <a name="terminology"></a>用語  
 描述虛擬模組分割時會使用下列詞彙：  
  
 容器模組或容器  
 彙總模組。  
  
 子模組或虛擬模組  
 在容器中找到的模組。  
  
 一般模組  
 建置時間未合併的模組。 這些模組不是容器模組，就是子模組。  
  
 ICorDebugModule 介面物件將代表容器模組和子模組。 不過，介面的行為都稍有不同，在每個案例中，為\<to x section> > 一節將說明。  
  
## <a name="modules-and-assemblies"></a>模組和組件  
 組件合併案例不支援多模組組件，因此模組和組件之間有一對一關聯性。 每個 ICorDebugModule 物件，不論代表容器模組或子模組，都有對應的 ICorDebugAssembly 物件。 [Icordebugmodule:: Getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法會從模組將組件。 若要將其他方向的對應[icordebugassembly:: Enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)方法會列舉 1 個模組。 由於組件和模組在此情況下會形成緊密結合的配對，因此組件和模組兩個詞彙的互換情況會更高。  
  
## <a name="behavioral-differences"></a>行為的差異  
 容器模組具有下列行為和特性：  
  
- 所有構成子模組的中繼資料會合併在一起。  
  
- 其類型名稱可能會受損。  
  
- [Icordebugmodule:: Getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法傳回的磁碟上模組的路徑。  
  
- [Icordebugmodule:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法會傳回該映像的大小。  
  
- ICorDebugAssembly3.EnumerateContainedAssemblies 方法會列出子模組。  
  
- ICorDebugAssembly3.GetContainerAssembly 方法會傳回 `S_FALSE`。  
  
 子模組具有下列行為和特性：  
  
- 子模組包含一組縮減的中繼資料，只對應至已合併的原始組件。  
  
- 中繼資料名稱不會受損。  
  
- 中繼資料語彙基元不太可能符合原始組件在建置流程中合併前的語彙基元。  
  
- [Icordebugmodule:: Getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法會傳回組件名稱，而不是檔案路徑。  
  
- [Icordebugmodule:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法會傳回原始未合併的映像大小。  
  
- ICorDebugModule3.EnumerateContainedAssemblies 方法會傳回 `S_FALSE`。  
  
- ICorDebugAssembly3.GetContainerAssembly 方法會傳回所包含的模組。  
  
## <a name="interfaces-retrieved-from-modules"></a>從模組擷取的介面  
 可從模組建立或擷取的各種介面。 其中包括：  
  
- ICorDebugClass 物件由[icordebugmodule:: Getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)方法。  
  
- ICorDebugAssembly 物件由[icordebugmodule:: Getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法。  
  
 這些物件一律會快取[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)，所以會有相同的指標識別，不論是否已建立或查詢的目標容器模組或子模組。 子模組提供這些快取物件的篩選檢視，而不是其本身複本的個別快取。  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>虛擬模組分割和未受管理的偵錯 API  
 下表顯示虛擬模組分割如何影響未受管理之偵錯 API 中其他方法的行為。  
  
|方法|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|傳回這個函式原本定義所在的子模組|傳回已合併這個函式的目標容器模組|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|傳回這個類別原本定義所在的子模組|傳回已合併這個類別的目標容器模組。|  
|ICorDebugModuleDebugEvent::GetModule|傳回已載入的容器模組。 不論這個設定為何，都不會提供載入事件給子模組。|傳回已載入的容器模組。|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|傳回子組件和一般組件的清單，不包含任何容器組件。 **注意：** 如有任何容器組件遺漏符號，則不會列舉其子組件。 如有任何一般組件遺漏符號，則列舉或不列舉都有可能。|傳回容器組件和一般組件的清單，不包含任何子組件。 **注意：** 如有任何一般組件遺漏符號，則列舉或不列舉都有可能。|  
|[Icordebugcode:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) （參考時，僅限 IL 程式碼）|傳回在預先合併組件映像中有效的 IL。 具體來說，當所參考的類型未在包含 IL 的虛擬模組中定義時，所有內嵌中繼資料語彙基元都會是正確的 TypeRef 或 MemberRef 語彙基元。 可以查閱這些 TypeRef 或 memberref 語彙基元[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)對應的虛擬 ICorDebugModule 物件的物件。|傳回合併後組件映像中的 IL。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess6 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
