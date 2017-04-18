---
title: "套用 Interop 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, 將元件公開到 COM"
  - "屬性 [.NET Framework], 轉換工具"
  - "屬性 [.NET Framework], 設計階段功能"
  - "屬性 [.NET Framework], Interop 特有"
  - "COM Interop, 套用屬性"
  - "COM Interop, 公開 COM 元件"
  - "轉換工具屬性"
  - "設計階段屬性"
  - "與 Unmanaged 程式碼的互通, 套用屬性"
  - "與 Unmanaged 程式碼的互通, 公開 .NET Framework 元件"
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 套用 Interop 屬性
The <xref:System.Runtime.InteropServices> 命名空間提供了三種類別的 Interop 相關屬性：一種是您在設計階段套用的屬性、一種是 COM Interop 工具和 API 在轉換過程中套用的屬性，還有一種是您或 COM Interop 套用的屬性。  
  
 如果您不熟悉將屬性套用至 Managed 程式碼的工作，請參閱[使用屬性擴充中繼資料](../../../docs/standard/attributes/index.md)。  就像其他自訂屬性一樣，您可以將 Interop 專屬屬性 \(Attribute\) 套用至型別、方法、屬性 \(Property\)、參數、欄位和其他成員。  
  
## 設計階段屬性  
 您可以使用設計階段屬性來調整 COM Interop 工具和 API 所執行的轉換處理結果。  下表所述是您能夠套用至 Managed 原始程式碼的屬性。  COM Interop 工具偶爾也會套用下表所述的屬性。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|指定型別是否要使用 Automation 封送處理器或自訂的 Proxy 和 Stub 來封送處理。|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|控制對類別所產生之介面的型別。|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|辨識從型別程式庫匯入原始 Coclass 的 CLSID。<br /><br /> COM Interop 工具通常都會套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|表示已從 COM 型別程式庫匯入 Coclass 或介面定義。  Runtime 會使用這個旗標來了解如何啟動和封送處理該型別。  這個屬性禁止將型別重新匯回型別程式庫中。<br /><br /> COM Interop 工具通常都會套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|指示當組件已註冊為從 COM 使用時應該呼叫某個方法，讓使用者撰寫的程式碼能夠在註冊處理時被執行。|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|識別類別之事件來源的介面。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|指示當組件從 COM 移除註冊時應該呼叫某個方法，讓使用者撰寫的程式碼能夠在這項處理時被執行。|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|當屬性值等於 **false** 時，將型別轉譯為讓 COM 看不見。  這個屬性可以套用至個別型別或套用至整個組件以控制 COM 的可視性。  根據預設，所有 Managed 公用型別都是可見的；不需要這個屬性來讓它們成為可見。|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|指定方法或欄位的 COM 分派識別項 \(Dispatch Identifier，DISPID\)。  這個屬性 \(Attribute\) 含有它所描述之方法、欄位或屬性 \(Property\) 的 DISPID。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|當配合 **StructLayoutAttribute** 使用且 **LayoutKind** 設定為 Explicit 時，指示每一欄位在類別中的實際位置。|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|指定類別、介面或整個型別程式庫的全域唯一識別項 \(GUID\)。  傳遞給屬性 \(Attribute\) 的字串必須是型別 **System.Guid** 可接受建構函式 \(Constructor\) 引數的格式。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|[IDispatchImpAttribute](frlrfsystemruntimeinteropservicesidispatchimplattributeclasstopic)|指示在公開雙重介面 \(Dual Interface\) 和分配介面 \(Dispinterface\) 給 COM 時，Common Language Runtime 所要使用的 **IDispatch** 介面實作。|  
|<xref:System.Runtime.InteropServices.InAttribute>|指示資料應封送處理進入呼叫端。  可用於屬性參數。|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|控制 Managed 介面如何公開給 COM 用戶端 \(僅適用於 Dual、IUnknown 所衍生或 IDispatch\)。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|指示 Unmanaged 方法簽章需要 LCID 參數。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|指示欄位或參數中的資料在 Managed 和 Unmanaged 程式碼之間應如何封送處理。  這個屬性必定是選擇性的，因為每種資料型別都有預設的封送處理行為。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|指示參數為選擇性的。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.OutAttribute>|指示欄位或參數中的資料必須從被呼叫的物件封送處理回其呼叫端。|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|抑制通常發生於互通呼叫的 HRESULT 或 Retval 簽章轉換。  這個屬性會影響封送處理以及型別程式庫匯出。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|指定 .NET Framework 類別的 ProgID。  可使用於屬性類別。|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|控制類別欄位的實體配置。<br /><br /> COM Interop 工具可以套用這個屬性。|  
  
## 轉換工具屬性  
 下表所述是 COM Interop 工具在轉換處理時套用的屬性。  您不能在設計階段套用這些屬性。  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|指示參數或欄位型別的 COM 別名 \(Alias\)。  可使用於屬性參數、欄位或傳回值。|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|指示類別或介面的相關資訊從型別程式庫匯入組件時遺失。|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|辨識實作事件介面方法的來源介面和類別。|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|指示這個組件原來是從 COM 型別程式庫所匯入的。  這個屬性含有原來型別程式庫的型別程式庫定義。|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|含有原來針對這個函式從 COM 型別程式庫匯入的 **FUNCFLAGS**。|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|含有原來針對這個型別從 COM 型別程式庫匯入的 **TYPEFLAGS**。|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|含有原來針對這個變數從 COM 型別程式庫匯入的 **VARFLAGS**。|  
  
## 請參閱  
 <xref:System.Runtime.InteropServices>   
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [屬性](../../../docs/standard/attributes/index.md)   
 [限定互通的 .NET 類型](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)   
 [封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)