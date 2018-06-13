---
title: 套用 Interop 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- design-time attributes
- .NET Framework, exposing components to COM
- attributes [.NET Framework], design-time functionality
- conversion-tool attributes
- attributes [.NET Framework], interop-specific
- attributes [.NET Framework], conversion-tool
- interoperation with unmanaged code, applying attributes
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
- COM interop, applying attributes
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 554ea7c54973852510e539000baf03bdce8e7bcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392560"
---
# <a name="applying-interop-attributes"></a>套用 Interop 屬性
<xref:System.Runtime.InteropServices> 命名空間提供了三種類別的 Interop 專屬屬性：一種是您在設計階段套用的屬性、一種是 COM Interop 工具和 API 在轉換過程中套用的屬性，還有一種是您或 COM Interop 套用的屬性。  
  
 如果您不熟悉將屬性套用至 Managed 程式碼的工作，請參閱[使用屬性擴充中繼資料](../../../docs/standard/attributes/index.md)。 就像其他自訂屬性一樣，您可以將 Interop 專屬屬性 (attribute) 套用至類型、方法、屬性 (property)、參數、欄位和其他成員。  
  
## <a name="design-time-attributes"></a>設計階段屬性  
 您可以使用設計階段屬性來調整 COM Interop 工具和 API 所執行的轉換處理結果。 下表描述您可以套用到 Managed 原始程式碼的屬性。 COM Interop 工具偶爾也會套用下表所述的屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|指定類型是否應使用 Automation 封送處理器或自訂的 Proxy 和 Stub 來進行封送處理。|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|控制對類別所產生之介面的類型。|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|識別從型別程式庫匯入之原始 Coclass 的 CLSID。<br /><br /> COM Interop 工具通常都會套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|表示已從 COM 類型程式庫匯入 Coclass 或介面定義。 執行階段會使用這個旗標來了解如何啟動和封送處理該類型。 這個屬性禁止將類型重新匯回型別程式庫中。<br /><br /> COM Interop 工具通常都會套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|表示當組件已註冊為從 COM 使用時應該呼叫某個方法，讓使用者撰寫的程式碼能夠在註冊處理期間執行。|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|識別此類別之事件來源的介面。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|表示當組件從 COM 取消註冊時應該呼叫某個方法，讓使用者撰寫的程式碼能夠在處理期間執行。|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|當屬性值等於 **false** 時，將類型轉譯為讓 COM 看不見。 這個屬性可以套用至個別類型或套用至整個組件以控制 COM 的可視性。 根據預設，所有 Managed 公用類型都是可見的；不需要這個屬性來讓它們變成可見。|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|指定方法或欄位的 COM 分派識別碼 (DISPID)。 這個屬性 (attribute) 含有它所描述之方法、欄位或屬性 (property) 的 DISPID。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|當搭配 **StructLayoutAttribute** 使用且 **LayoutKind** 設定為 Explicit 時，指出每一欄位在類別中的實際位置。|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|指定類別、介面或整個型別程式庫的全域唯一識別碼 (GUID)。 傳遞給屬性的字串必須是類型 **System.Guid** 可接受的建構函式引數的格式。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|表示在公開雙重介面 (Dual Interface) 和分配介面 (Dispinterface) 給 COM 時，通用語言執行平台所使用的 **IDispatch** 介面實作。|  
|<xref:System.Runtime.InteropServices.InAttribute>|表示資料應封送處理至呼叫端。 可用於屬性參數。|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|控制 Managed 介面如何公開給 COM 用戶端 (僅適用於 Dual、IUnknown-derived 或 IDispatch)。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|表示 Unmanaged 方法簽章預期有 LCID 參數。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|表示欄位或參數中的資料在 Managed 和 Unmanaged 程式碼之間應如何封送處理。 這個屬性一律為選擇性屬性，因為每種資料類型都有預設的封送處理行為。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|表示參數為選擇性。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.OutAttribute>|表示欄位或參數中的資料必須從呼叫的物件封送處理回其呼叫端。|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|抑制通常發生於互通呼叫期間的 HRESULT 或 Retval 簽章轉換。 這個屬性會影響封送處理以及型別程式庫匯出。<br /><br /> COM Interop 工具可以套用這個屬性。|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|指定 .NET Framework 類別的 ProgID。 可用於屬性類別。|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|控制類別欄位的實體配置。<br /><br /> COM Interop 工具可以套用這個屬性。|  
  
## <a name="conversion-tool-attributes"></a>轉換工具屬性  
 下表描述 COM Interop 工具在轉換處理期間套用的屬性。 您不會在設計階段套用這些屬性。  
  
|屬性|描述|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|表示參數或欄位類型的 COM 別名。 可用於屬性參數、欄位或傳回值。|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|表示類別或介面的相關資訊在從型別程式庫匯入組件時遺失。|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|識別實作事件介面方法的來源介面和類別。|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|表示這個組件原來是從 COM 類型程式庫匯入的。 這個屬性含有原來型別程式庫的型別程式庫定義。|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|含有原來針對這個函式從 COM 類型程式庫匯入的 **FUNCFLAGS**。|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|含有原來針對這個類型從 COM 型別程式庫匯入的 **TYPEFLAGS**。|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|含有原來針對這個變數從 COM 類型程式庫匯入的 **VARFLAGS**。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.InteropServices>  
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [屬性](../../../docs/standard/attributes/index.md)  
 [限定互通的 .NET 類型](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
