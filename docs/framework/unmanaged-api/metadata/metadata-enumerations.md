---
title: 中繼資料列舉
ms.date: 03/30/2017
helpviewer_keywords:
- enumerations [.NET Framework metadata]
- metadata enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], metadata
ms.assetid: 711ab251-cfdb-4280-aaa6-9bc1b341cdc3
ms.openlocfilehash: 2409998c53aee8cb76e66cbc9a6cd92ad9fb6cd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489617"
---
# <a name="metadata-enumerations"></a>中繼資料列舉
本節描述中繼資料應用程式開發介面所使用的 Unmanaged 列舉。  
  
## <a name="in-this-section"></a>本節內容  
 [AssemblyFlags 列舉](assemblyflags-enumeration.md)  
 包含值，這些值描述組件的執行階段功能。  
  
 [AssemblyRefFlags 列舉](assemblyrefflags-enumeration.md)  
 包含值，這些值描述組件參考的功能。  
  
 [CeeSectionAttr 列舉](ceesectionattr-enumeration.md)  
 提供值，指定區段的屬性，以供[ICeeGen](iceegen-interface.md)介面使用。  
  
 [CeeSectionRelocType 列舉](ceesectionreloctype-enumeration.md)  
 提供值，以影響 `reloc` 呼叫[ICeeGen：： AddSectionReloc](iceegen-addsectionreloc-method.md)方法時所發出的指令類型。  
  
 [COINITICOR 列舉](coiniticor-enumeration.md)  
 指定初始化 common language runtime 時， [CoInitializeCor](../hosting/coinitializecor-function.md)所使用的常數。  
  
 [COINITIEE 列舉](coinitiee-enumeration.md)  
 指定初始化 common language runtime 時， [CoInitializeEE](../hosting/coinitializeee-function.md)所使用的常數。  
  
 [CorArgType 列舉](corargtype-enumeration.md)  
 包含值，這些值描述執行階段控制代碼的原生類型。  
  
 [CorAssemblyFlags 列舉](corassemblyflags-enumeration.md)  
 包含值，這些值描述套用至組件編譯的中繼資料。  
  
 [CorAttributeTargets 列舉](corattributetargets-enumeration.md)  
 指定有效套用屬性的應用程式項目。  
  
 [CorCallingConvention 列舉](corcallingconvention-enumeration.md)  
 包含值，這些值描述在 Managed 程式碼中進行的呼叫慣例類型。  
  
 [CorCheckDuplicatesFor 列舉](corcheckduplicatesfor-enumeration.md)  
 包含值，可在檢查期間用來檢查是否有重複項目。  
  
 [CorDeclSecurity 列舉](cordeclsecurity-enumeration.md)  
 包含值，這些值描述 Common Language Runtime 所使用的宣告式安全性類型。  
  
 CorElementType  
 包含值，這些值描述 Common Language Runtime <xref:System.Type> 的基礎原生類型。  
  
 [CorErrorIfEmitOutOfOrder 列舉](corerrorifemitoutoforder-enumeration.md)  
 包含旗標值，這些值表示中繼資料未按順序發出時，在哪些條件下應該產生錯誤訊息。  
  
 [CorEventAttr 列舉](coreventattr-enumeration.md)  
 包含值，這些值描述事件的中繼資料。  
  
 [CorFieldAttr 列舉](corfieldattr-enumeration.md)  
 包含值，這些值描述與欄位有關的中繼資料。  
  
 [CorFileFlags 列舉](corfileflags-enumeration.md)  
 包含值，描述在[IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md)方法的呼叫中定義的檔案類型。  
  
 [CorFileMapping 列舉](corfilemapping-enumeration.md)  
 包含值，描述從[IMetaDataInfo：： GetFileMapping](imetadatainfo-getfilemapping-method.md)方法的呼叫所傳回的檔對應類型。  
  
 [CorGenericParamAttr 列舉](corgenericparamattr-enumeration.md)  
 包含值，描述 <xref:System.Type> 泛型型別的參數，如同[IMetaDataEmit2：:D efinegenericparam](imetadataemit2-definegenericparam-method.md)方法的呼叫中所使用。  
  
 [CorImportOptions 列舉](corimportoptions-enumeration.md)  
 包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。  
  
 [CorLinkerOptions 列舉](corlinkeroptions-enumeration.md)  
 指定旗標，以選取中繼資料連結器的選項。  
  
 [CorLocalRefPreservation 列舉](corlocalrefpreservation-enumeration.md)  
 包含代表本機參考處理方式的旗標值。  
  
 [CorManifestResourceFlags 列舉](cormanifestresourceflags-enumeration.md)  
 包含值，這些值描述編碼在組件資訊清單中的資源可視性。  
  
 [CorMethodAttr 列舉](cormethodattr-enumeration.md)  
 包含值，這些值描述與方法有關的中繼資料。  
  
 [CorMethodImpl 列舉](cormethodimpl-enumeration.md)  
 包含值，這些值描述方法實作功能。  
  
 [CorMethodSemanticsAttr 列舉](cormethodsemanticsattr-enumeration.md)  
 包含值，這些值描述方法與關聯的屬性或事件之間的關聯性。  
  
 [CorNativeLinkFlags 列舉](cornativelinkflags-enumeration.md)  
 提供連結器在連結機器碼時所使用的旗標值。  
  
 [CorNativeLinkType 列舉](cornativelinktype-enumeration.md)  
 提供值，這些值表示機器碼中已連結的類型。  
  
 [CorNativeType 列舉](cornativetype-enumeration.md)  
 包含值，這些值描述原生 Unmanaged 類型。  
  
 [CorNotificationForTokenMovement 列舉](cornotificationfortokenmovement-enumeration.md)  
 包含旗標值，這些值會影響語彙基元移動時的通知。  
  
 [CorOpenFlags 列舉](coropenflags-enumeration.md)  
 包含在開啟資訊清單檔案時控制中繼資料行為的旗標值。  
  
 [CorParamAttr 列舉](corparamattr-enumeration.md)  
 包含值，這些值描述方法參數的中繼資料。  
  
 [CorPEKind 列舉](corpekind-enumeration.md)  
 包含值，描述從[IMetaDataImport2：： GetPEKind](imetadataimport2-getpekind-method.md)方法的呼叫傳回的可攜式可執行檔。  
  
 [CorPinvokeMap 列舉](corpinvokemap-enumeration.md)  
 包含值，這些值會描述 PInvoke 呼叫的功能。  
  
 [CorPropertyAttr 列舉](corpropertyattr-enumeration.md)  
 包含值，這些值描述屬性的中繼資料。  
  
 [CorRefToDefCheck 列舉](correftodefcheck-enumeration.md)  
 指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。  
  
 [CorRegFlags 列舉](corregflags-enumeration.md)  
 提供安裝模組或組合時，用於註冊的旗標值。  
  
 [CorSaveSize 列舉](corsavesize-enumeration.md)  
 包含值，這些值表示在查詢儲存作業的大小時所需的精確度等級。  
  
 [CorSerializationType 列舉](corserializationtype-enumeration.md)  
 包含值，這些值描述 Common Language Runtime 如何將物件序列化。 這些值通常會對應至 CorElementType 值。  
  
 [CorSetENC 列舉](corsetenc-enumeration.md)  
 包含值，可用來在中繼資料產生期間影響行為。  
  
 [CorThreadSafetyOptions 列舉](corthreadsafetyoptions-enumeration.md)  
 指定旗標，以選取執行緒安全的選項。  
  
 [CorTokenType 列舉](cortokentype-enumeration.md)  
 包含值，這些值表示中繼資料語彙基元所參考的物件類型。  
  
 [CorTypeAttr 列舉](cortypeattr-enumeration.md)  
 包含值，這些值表示類型中繼資料。  
  
 [CorUnmanagedCallingConvention 列舉](corunmanagedcallingconvention-enumeration.md)  
 包含值，這些值描述 Unmanaged 呼叫慣例。  
  
 [CorValidatorModuleType 列舉](corvalidatormoduletype-enumeration.md)  
 提供[IMetaDataValidate](imetadatavalidate-interface.md)介面用來指定模組類型（PE 檔案與 .obj 檔案）的值。  
  
 [COUNINITIEE 列舉](couninitiee-enumeration.md)  
 指定初始化 common language runtime 時， [CoUninitializeEE](../hosting/couninitializeee-function.md)所使用的常數。  
  
## <a name="related-sections"></a>相關章節  
 [中繼資料介面](metadata-interfaces.md)  
  
 [中繼資料全域靜態函式](metadata-global-static-functions.md)  
  
 [中繼資料結構](metadata-structures.md)  
  
 [中繼資料等位](metadata-unions.md)
