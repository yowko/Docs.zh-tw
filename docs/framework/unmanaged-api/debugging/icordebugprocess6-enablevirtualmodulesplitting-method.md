---
title: ICorDebugProcess6::EnableVirtualModuleSplitting 方法
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178563"
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
 虛擬模組拆分導致[ICorDebug](icordebug-interface.md)識別在生成過程中合併在一起的模組，並將其作為一組單獨的模組而不是單個大型模組呈現。 這樣做會更改下面描述的各種[ICorDebug](icordebug-interface.md)方法的行為。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
 您可以呼叫這個方法並隨時變更 `enableSplitting` 的值。 它不會在[ICorDebug](icordebug-interface.md)物件中導致任何有狀態的功能更改，除了更改[調用虛擬模組拆分和非託管調試 API](#APIs)部分中列出的方法的行為。 呼叫這些方法時，使用虛擬模組確實會對效能帶來負面影響。 此外，可能需要大量虛擬化中繼資料的記憶體緩存才能正確實現[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) API，即使在關閉虛擬模組拆分後，這些緩存也可能保留。  
  
## <a name="terminology"></a>詞彙  
 描述虛擬模組分割時會使用下列詞彙：  
  
 容器模組或容器  
 彙總模組。  
  
 子模組或虛擬模組  
 在容器中找到的模組。  
  
 一般模組  
 建置時間未合併的模組。 這些模組不是容器模組，就是子模組。  
  
 容器模組和子模組都會以 ICorDebugModule 介面物件來代表。 但是，介面的行為在每種情況下都略有不同，如第>節的\<xref 描述。  
  
## <a name="modules-and-assemblies"></a>模組和組件  
 組件合併案例不支援多模組組件，因此模組和組件之間有一對一關聯性。 每個 ICorDebugModule 物件不論代表容器模組或子模組，都有對應的 ICorDebugAssembly 物件。 [ICorDebugModule：獲取組裝](icordebugmodule-getassembly-method.md)方法從模組轉換為程式集。 要向其他方向映射[，ICorDebugAssembly：：枚舉模組](icordebugassembly-enumeratemodules-method.md)方法僅枚舉 1 個模組。 由於組件和模組在此情況下會形成緊密結合的配對，因此組件和模組兩個詞彙的互換情況會更高。  
  
## <a name="behavioral-differences"></a>行為差異  
 容器模組具有下列行為和特性：  
  
- 所有構成子模組的中繼資料會合併在一起。  
  
- 其類型名稱可能會受損。  
  
- [ICorDebugModule：：GetName](icordebugmodule-getname-method.md)方法返回磁片模組的路徑。  
  
- [ICorDebugModule：GetSize](icordebugmodule-getsize-method.md)方法返回該圖像的大小。  
  
- ICorDebugAssembly3.EnumerateContainedAssemblies 方法會列出子模組。  
  
- ICorDebugAssembly3.GetContainerAssembly 方法會傳回 `S_FALSE`。  
  
 子模組具有下列行為和特性：  
  
- 子模組包含一組縮減的中繼資料，只對應至已合併的原始組件。  
  
- 中繼資料名稱不會受損。  
  
- 中繼資料語彙基元不太可能符合原始組件在建置流程中合併前的語彙基元。  
  
- [ICorDebugModule：getName](icordebugmodule-getname-method.md)方法返回程式集名稱，而不是檔路徑。  
  
- [ICorDebugModule：GetSize](icordebugmodule-getsize-method.md)方法返回原始未合併的圖像大小。  
  
- ICorDebugModule3.EnumerateContainedAssemblies 方法會傳回 `S_FALSE`。  
  
- ICorDebugAssembly3.GetContainerAssembly 方法會傳回所包含的模組。  
  
## <a name="interfaces-retrieved-from-modules"></a>從模組擷取的介面  
 可從模組建立或擷取的各種介面。 其中包含：  
  
- ICorDebugClass 物件，由[ICorDebugModule 返回：：獲取ClassFromToken](icordebugmodule-getclassfromtoken-method.md)方法。  
  
- ICorDebugAssembly 物件，由[ICorDebugModule：getAssembly](icordebugmodule-getassembly-method.md)方法返回。  
  
 這些物件始終由[ICorDebug](icordebug-interface.md)緩存，無論它們是從容器模組還是子模組創建還是查詢它們，它們都將具有相同的指標標識。 子模組提供這些快取物件的篩選檢視，而不是其本身複本的個別快取。  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>虛擬模組分割和未受管理的偵錯 API  
 下表顯示虛擬模組分割如何影響未受管理之偵錯 API 中其他方法的行為。  
  
|方法|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|傳回這個函式原本定義所在的子模組|傳回已合併這個函式的目標容器模組|  
|[ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|傳回這個類別原本定義所在的子模組|傳回已合併這個類別的目標容器模組。|  
|ICorDebugModuleDebugEvent::GetModule|傳回已載入的容器模組。 不論這個設定為何，都不會提供載入事件給子模組。|傳回已載入的容器模組。|  
|[ICorDebugAppDomain::EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|傳回子組件和一般組件的清單，不包含任何容器組件。 **注：** 如果缺少任何容器程式集，則不會枚舉其任何副程式集。 如有任何一般組件遺漏符號，則列舉或不列舉都有可能。|傳回容器組件和一般組件的清單，不包含任何子組件。 **注：** 如果缺少任何常規程式集，則可能會枚舉，也可能不枚舉。|  
|[ICorDebug代碼：獲取代碼](icordebugcode-getcode-method.md)（僅參考 IL 代碼時）|傳回在預先合併組件映像中有效的 IL。 具體來說，當所參考的類型未在包含 IL 的虛擬模組中定義時，所有內嵌中繼資料語彙基元都會是正確的 TypeRef 或 MemberRef 語彙基元。 這些 TypeRef 或成員Ref 權杖可以在[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件中為相應的虛擬 ICorDebugModule 物件進行備份。|傳回合併後組件映像中的 IL。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess6 介面](icordebugprocess6-interface.md)
- [偵錯介面](debugging-interfaces.md)
